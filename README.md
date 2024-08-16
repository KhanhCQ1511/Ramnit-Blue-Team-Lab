# Ramnit-Blue-Team-Lab

Link Lab: https://cyberdefenders.org/blueteam-ctf-challenges/ramnit

Tool: Volatility 3

### Q1: We need to identify the process responsible for this suspicious behavior. What is the name of the suspicious process?
#### ANS: ChromeSetup.exe

Use volatility tool to extract data from dmp file we have: 
![image](https://github.com/user-attachments/assets/a2b31bf7-cd86-45f0-99be-39524fbfdd80)

From there we get a file containing processes. However, after looking closely at the processes here, we do not get anything unusual
![image](https://github.com/user-attachments/assets/495c62ac-5128-4839-b38d-3ac21c47ba4c)

Switch to another analysis method still using this tool to count the computer's connections
![image](https://github.com/user-attachments/assets/d791e39d-c0a3-4d54-9f7b-05dfd010b6bd)

From here we get the IP addresses that the computer is connecting to
![image](https://github.com/user-attachments/assets/f3119ae6-920f-4761-841c-7e7a3cbbe68e)

Using VirusTotal to check these IP addresses and get a surprise
![image](https://github.com/user-attachments/assets/2e449889-6bf2-4a67-8a3a-5f746fcdd78d)

From here we can identify suspicious processes

### Q2: To eradicate the malware, what is the exact file path of the process executable?
#### ANS: C:\Users\alex\Downloads\ChromeSetup.exe

From the process file we can determine the path.
![image](https://github.com/user-attachments/assets/8234332e-208d-4bc3-99f1-a15966cd4375)

### Q3: Identifying network connections is crucial for understanding the malware's communication strategy. What is the IP address it attempted to connect to?
#### ANS: 58.64.204.181

From the connection statistics file we can determine this IP.
![image](https://github.com/user-attachments/assets/f0b6c6ba-c489-43ad-a2ac-5654eb6cff33)

### Q4: To pinpoint the geographical origin of the attack, which city is associated with the IP address the malware communicated with?
#### ANS: HONG KONG

![image](https://github.com/user-attachments/assets/8d6dfa92-ad4e-4962-b715-9ebf631aa0a7)

### Q5: Hashes provide a unique identifier for files, aiding in detecting similar threats across machines. What is the SHA1 hash of the malware's executable?
#### ANS: 280c9d36039f9432433893dee6126d72b9112ad2

Using the following command, we will get the image of the file we need mapped into memory
![image](https://github.com/user-attachments/assets/26f3b587-954a-4274-94c2-016d73132cf9)

From here we get the image of the malicious file
![image](https://github.com/user-attachments/assets/bff3264c-2e19-4486-b906-78804af2c906)

Using sha1sum to calculate the required sha1 hash
![image](https://github.com/user-attachments/assets/ce1ccc86-b17f-40e7-91ab-e1f52c58dbf2)

### Q6: Understanding the malware's development timeline can offer insights into its deployment. What is the compilation UTC timestamp of the malware?
#### ANS: 2019-12-01 08:36:04

You can check in VirusTotal:
![image](https://github.com/user-attachments/assets/fbc6d3d5-b20b-4076-bfed-8108e9c8a2af)

### Q7: Identifying domains involved with this malware helps in blocking future malicious communications and identifying current possible communications with that domain in our network. Can you provide the domain related to the malware?
#### ANS: dnsnb8.net

![image](https://github.com/user-attachments/assets/13b10232-e3e6-468e-b86f-41b1d8ac2147)
