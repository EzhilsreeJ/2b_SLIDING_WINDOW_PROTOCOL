# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```py
def send_frame(frame):
    # Simulate sending the frame to the server
    print(f"Sending frame: {frame}")
    return True  # Assume frame reaches the server successfully

def receive_ack():
    # Simulate receiving an ACK signal from the server
    return True  # Assume ACK received successfully

def main():
    try:
        frame_size = int(input("Enter the frame size: "))
        frame_number = 0

        while True:
            frame = f"Frame {frame_number}"
            if send_frame(frame):
                if receive_ack():
                    print(f"ACK received for {frame}")
                    frame_number += 1
                else:
                    print(f"ACK not received for {frame}. Resending...")
            else:
                print(f"Frame {frame} lost. Resending...")

    except ValueError:
        print("Invalid input. Please enter a valid frame size.")

if __name__ == "__main__":
    main()
```
## OUPUT
## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
