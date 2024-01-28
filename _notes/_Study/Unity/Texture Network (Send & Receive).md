## <mark style="background: #FFB8EBA6;">Base</mark>

- [f] <mark style="background: #BBFABBA6;">Sender Function </mark>
	- Render texture to Texture 2D
	- Texture2D to Byte Array
- [f] <mark style="background: #BBFABBA6;">Receive Function</mark>
	- Byte Array to Texture 2D
	- Texture 2D to Render Texture

## <mark style="background: #FFB8EBA6;">Network Method</mark>
- OSC 통신으로 하려고 했는나 Buffer size 문제
- texture 통신이다보니 byte array 중 하나만 누락이 되더라도 texture load가 되지 않는 문제점이 발생함
- [I] 따라서 OSC를 활용한 UDP 통신보다 TCPIP 통신이 더 적합하다고 생각함

## <mark style="background: #FFB8EBA6;">Network Issue</mark>
- Server 및 Client class를 기반으로 통신을 함
- Thread를 만들고 background로 돌려 계속 돌게 함
- On destroy() 를 했을 때 thread.abort() 함수를 통해 강제 종료함 
- 기존에는 thread.join() 을 통해 thread가 다 진행이 되고 종료하려고 했으나 종료되지 않는 문제가 있었음