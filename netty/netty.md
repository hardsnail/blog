#### 主要API
* Channel(通道):
* EventLoopGroup(事件循环组)：允许注册多个Channel，并且在事件循环时选择处理这些Channel，是特殊的EventExecutorGroup


A nexus to a network socket or a component which is capable of I/O
operations such as read, write, connect, and bind.
<p>
A channel provides a user:
<ul>
<li>the current state of the channel (e.g. is it open? is it connected?),</li>
<li>the {@linkplain ChannelConfig configuration parameters} of the channel (e.g. receive buffer size),</li>
<li>the I/O operations that the channel supports (e.g. read, write, connect, and bind), and</li>
<li>the {@link ChannelPipeline} which handles all I/O events and requests
    associated with the channel.</li>
</ul>

<h3>All I/O operations are asynchronous.</h3>
<p>
All I/O operations in Netty are asynchronous.  It means any I/O calls will
return immediately with no guarantee that the requested I/O operation has
been completed at the end of the call.  Instead, you will be returned with
a {@link ChannelFuture} instance which will notify you when the requested I/O
operation has succeeded, failed, or canceled.

<h3>Channels are hierarchical</h3>
<p>
A {@link Channel} can have a {@linkplain #parent() parent} depending on
how it was created.  For instance, a {@link SocketChannel}, that was accepted
by {@link ServerSocketChannel}, will return the {@link ServerSocketChannel}
as its parent on {@link #parent()}.
<p>
The semantics of the hierarchical structure depends on the transport
implementation where the {@link Channel} belongs to.  For example, you could
write a new {@link Channel} implementation that creates the sub-channels that
share one socket connection, as <a href="http://beepcore.org/">BEEP</a> and
<a href="http://en.wikipedia.org/wiki/Secure_Shell">SSH</a> do.

<h3>Downcast to access transport-specific operations</h3>
<p>
Some transports exposes additional operations that is specific to the
transport.  Down-cast the {@link Channel} to sub-type to invoke such
operations.  For example, with the old I/O datagram transport, multicast
join / leave operations are provided by {@link DatagramChannel}.

<h3>Release resources</h3>
<p>
It is important to call {@link #close()} or {@link #close(ChannelPromise)} to release all
resources once you are done with the {@link Channel}. This ensures all resources are
released in a proper way, i.e. filehandles.