# EX-NO-13-MESSAGE-AUTHENTICATION-CODE-MAC
## Submitted By:Ashwin Akash M
## Reference Number:212223230024
## AIM:
To implement MESSAGE AUTHENTICATION CODE(MAC)

## ALGORITHM:

### STEP:1 - Start by taking the secret key as input from the user.
→ Store the key in a character array to be used for MAC generation.
### STEP:2 - Ask the user to enter the message that needs authentication.
→ Store the message in another character array for processing.
### STEP:3 - Compute the MAC using a simple XOR operation between the key and message.
→ Repeat key and message characters if needed to fill a fixed MAC size (32 bytes).
→ Store the result in a MAC array and terminate it properly.
### STEP:4 - Display the computed MAC to the user in hexadecimal format.
→ Loop through the MAC array and print each byte as a two-digit hex value.
### STEP:5 - Receive the MAC value from the user that was sent or received separately.
→ Take input as hexadecimal values and store them in a received MAC array.
### STEP:6 - Compare the computed MAC with the received MAC to verify message integrity.
→ If they match, print that the message is authentic.
→ Otherwise, indicate that the message may have been tampered with.

## Program:
```
#include <stdio.h>
#include <string.h>
#define MAC_SIZE 32
void computeMAC(const char *key, const char *message, char *mac)
{
int key_len = strlen(key);
int msg_len = strlen(message);
for (int i = 0; i < MAC_SIZE; i++)
{
mac[i] = key[i % key_len] ^ message[i % msg_len];
}
mac[MAC_SIZE] = '\0';
}
int main()
{
char key[100], message[100];
char mac[MAC_SIZE + 1];
char receivedMAC[MAC_SIZE + 1];
printf("Enter the secret key: ");
scanf("%s", key);
printf("Enter the message: ");
scanf("%s", message);
computeMAC(key, message, mac);
printf("Computed MAC (in hex): ");
for (int i = 0; i < MAC_SIZE; i++)
{
printf("%02x", (unsigned char)mac[i]);
}
printf("\n");
printf("Enter the received MAC (as hex): ");
for (int i = 0; i < MAC_SIZE; i++)
{
scanf("%02hhx", &receivedMAC[i]);
}
if (memcmp(mac, receivedMAC, MAC_SIZE) == 0)
{
printf("MAC verification successful. Message is authentic.\n");
} else
{
printf("MAC verification failed. Message is not authentic.\n");
}
return 0;
}
```


## Output:
![Screenshot 2025-04-19 141236](https://github.com/user-attachments/assets/daaf34fe-4685-4e52-9ffd-ace022235494)

![Screenshot 2025-04-19 141257](https://github.com/user-attachments/assets/4abaa832-085b-444c-b9d2-0ed64cbff268)

## Result:
The program is executed successfully.
