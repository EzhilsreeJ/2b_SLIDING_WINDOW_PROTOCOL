# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:
To Write python program to perform stop and wait protocol.
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```py
import time

def sender(frames, window_size):
    base = 0
    next_seq_num = 0

    while base < len(frames):
        for i in range(base, min(base + window_size, len(frames))):
            print(f"Sending Frame {next_seq_num}: {frames[i]}")
            next_seq_num += 1

        ack_received = False
        while not ack_received:
            ack = input("Enter ACK number received from server: ")
            if ack.isdigit() and base <= int(ack) < next_seq_num:
                base = int(ack) + 1
                ack_received = True
            else:
                print("Invalid ACK. Resending frames...")

def receiver(frames, window_size):
    expected_frame = 0

    while expected_frame < len(frames):
        for i in range(expected_frame, min(expected_frame + window_size, len(frames))):
            print(f"Received Frame {i}: {frames[i]}")
            time.sleep(1)  # Simulating processing time
            print(f"Sending ACK for Frame {i}")
            time.sleep(1)  # Simulating transmission time
            print(f"ACK {i} sent")

        expected_frame += window_size

if __name__ == "__main__":
    frame_size = int(input("Enter frame size: "))
    frames = [f"Frame {i}" for i in range(frame_size)]

    window_size = int(input("Enter window size: "))

    print("Sender:")
    sender(frames, window_size)

    print("\nReceiver:")
    receiver(frames, window_size)

    print("Program stopped.")

```
## OUPUT

![image](https://github.com/EzhilsreeJ/2b_SLIDING_WINDOW_PROTOCOL/assets/144870412/ee52ec65-d169-4279-a301-7798cac3c463)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
