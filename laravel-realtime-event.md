////////////laravel reverb start/////////////////
```bash
   php artisan install:broadcasting
```
if stops 
npm install --save-dev laravel-echo pusher-js && npm run build

start revarb
```bash
   php artisan reverb:start --debug
```

start queue
```bash
   php artisan queue:listen
```
   npm run dev

   include this in file
   @vite(['resources/css/app.css', 'resources/js/app.js'])

   php artisan make:event ChatSent

   ChatSent::dispatch($request->message,$request->sender);

       <script
			  src="https://code.jquery.com/jquery-3.7.1.js"
			  integrity="sha256-eKhayi8LEQwp4NKxN+CfCh+3qOVUtJn3QNZ0TciWLP4="
			  crossorigin="anonymous">
    </script>

    <script>
        function sendMessage() {
            var sender = "{{$username}}";
            var message = $('#messageinput').val();
            var csrfToken = "{{ csrf_token() }}";
            //alert(sernder);
            $.ajax({
                url: "{{ route('chat.room.send') }}",
                type: "POST",
                headers: {
                    'X-CSRF-TOKEN': csrfToken
                },
                data: {
                    sender: sender,
                    message: message,
                    _token: csrfToken
                },
                success: function (response) {
                    $('#messageinput').val("");
                    $('#messages').append('<div class="message sent" style="text-align: right;">' + response.message + '</div>');
                },
                error: function (xhr, status, error) {
                    console.error(xhr.responseText);
                }
            });
        }
        window.onload = () => {
            Echo.channel('chat-room')
            .listen('ChatSent', (e) => {
                //alert(e.sender);
                if(e.sender != "{{$username}}") {
                    $('#messages').append('<div class="message received" style="text-align: left;">' + e.message + '</div>');
                }

            });
        }
    </script>

    use Illuminate\Contracts\Broadcasting\ShouldBroadcast;

    class ChatSent implements ShouldBroadcast
{
    use Dispatchable, InteractsWithSockets, SerializesModels;

    /**
     * Create a new event instance.
     */
    public function __construct(
        public string $message,
        public string $sender
    )
    {
        //
    }

    /**
     * Get the channels the event should broadcast on.
     *
     * @return array<int, \Illuminate\Broadcasting\Channel>
     */
    public function broadcastOn(): array
    {
        return [
            new Channel('chat-room'),
        ];
    }
}

////////////laravel reverb end//////////////////