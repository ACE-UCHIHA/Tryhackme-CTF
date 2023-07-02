<img src="/img/img1.PNG"><br>

# Table of Contents

- [Task 1](#lets-start-from-task-1-in-task-1-theyre-telling-you-to-dowload-the-pcapng-file-so-obviously-download-it)
- [Task 2](#now-lets-get-into-task-2-in-task-2-the-first-question-is-)
  -    [Q1](#q1-when-was-the-first-packet-captured-format--year-month-date-hoursminutesseconds)
  -    [Q2](#q2-when-was-the-last-packet-captured-format--year-month-date-hoursminutesseconds)
  -    [Q3](#q3-how-many-packets-were-captured)
  -    [Q4](#q4-what-is-the-sha256-hash-of-the-file)
  -    [Q5](#q5-what-is-the-md5-hash-of-the-file)
- [Task 3](#task-3)
  -    [Q1](#q1-how-many-icmp-packets-were-captured-with-parcentage)
  -    [Q2](#q2-there-was-an-icmp-ping-request-packet-which-did-not-receive-any-response-back-what-is-the-packet-number)
  -    [Q3](#q3-what-was-thr-source-ip-of-the-above-packet)
  -    [Q4](#q4-what-was-thr-destination-ip-of-the-above-packet)
  -    [Q5](#q5-what-is-the-length-of-the-packet)
  -    [Q6](#q6-in-which-country-standard-time-was-the-packet-captured)
  -    [Q7](#q7--when-the-packet-was-captured-format--year-month-date-hoursminutesseconds)
  -    [Q8](#q8-what-is-the-data-value-of-the-packet)
  -    [Q9](#q9-decode-the-value)
  -    [Q10](#q10-in-the-decoded-strings-there-was--an-username-and-a-password-what-are-those)          
- [Task 4](#task-4)
  -    [Q1](#q1--how-many-ftp-packets-were-captured-with-parcentage)
  -    [Q2](#q2-what-was-the-users-first-username-and-password-that-tried-to-login-to-frp-server-format-usernamepassword)
  -    [Q3](#q3-what-was-the-users-last-username-and-password-that-tried-to-login-to-frp-server-format-usernamepassword)
  -    [Q4](#q4-what-was-the-users-last-username-and-password-that-tried-to-login-to-frp-server-format-usernamepassword)
  -    [Q5](#q5-which-file-is-seems-to-be-malicious-format-file-extension)
  -    [Q6](#q6-what-is-the-md5-hash-of-the-malicious-file)
  -    [Q7](#q7-what-is-the-md5-hash-of-the-normal-file)
  -    [Q8](#q8-what-is-the-file-size-of-malicious-file-format-in-bytes)
  -    [Q9](#q9-what-is-the-file-size-of-noraml-file-format-in-bytes)
  -    [Q10](#q10-in-which-which-directory-was-the-normal-file-located)
  -    [Q11](#q11-in-which-which-directory-was-the-malicious-file-located)
  -    [Q12](#q12-what-is-the-ip-of-the-device-that-was-infected-by-the-malicious-file)
- [Task 5](#)





## Let's start from Task 1. In task 1 they're telling you to dowload the pcapng file so obviously download it.

## Now let's get into Task 2. In Task 2 the first question is : 
#### Q1: When was the first packet captured? (Format : Year-Month-Date Hours:Minutes:Seconds)

Okey so we have to open the thmcaptureh4x0r3rr0r.pcapng file in wireshark then we'll see a packet at the top which is no 1 ( numbers are defined in the left first column). After selecting the first file we have to look at the " Packet Details Pane " . If we drop down the first row "Frame 1:" we'll be able to see the content that was in the Frame 1 . If we look at the contents we'll see a row named Arrival time.
There you'll get the answer of the Q1.

<img src="/img/img2.PNG"><br>


#### Q2: When was the last packet captured? (Format : Year-Month-Date Hours:Minutes:Seconds)

This is similar to the Q1 all you have to do is just naviagte to the bottom of the list and select the last packet and look for the dat & time like you did in the Q1.
<img src="/img/img3.PNG"><br>

#### Q3: How many packets were captured?

To see how many packets were captured you have look at the bottom of you're wiresahrk UI thre is a status bar there. There you should see how many packets are there and many the displayed.
<img src="/img/img4.PNG"><br>

#### Q4: What is the SHA256 hash of the file?

To get the SHA256 hash of a file first select the file then look at the top of you're wireshark UI. There is a Toolbar. On the toolbar click the Statistics option then click the capture file properties or you can use  Ctrl+Alt+Shift+C and a page should pop up there you'll be able the find the SHA256 hash.
<img src="/img/img5.PNG"><br>
<img src="/img/img6.png"><br>
<img src="/img/img7.PNG"><br>

 #### Q5: What is the MD5 hash of the file?

So I used a Python script to get the hash. here's the script:

### MD5 encryption py script

```python
import hashlib

def calculate_md5(file_path):
    with open(file_path, 'rb') as f:
        md5_hash = hashlib.md5()
        for chunk in iter(lambda: f.read(4096), b''):
            md5_hash.update(chunk)
    return md5_hash.hexdigest()

extracted_file_path = r'path/to/your/pcapng/file'
md5_hash = calculate_md5(extracted_file_path)
print("MD5 Hash:", md5_hash)
```


## Task 3
#### Q1: How many ICMP packets were captured? (with parcentage)

This is similar to the [Task 2](#now-lets-get-into-task-2-in-task-2-the-first-question-is-) [Q3](#q3-how-many-packets-were-captured) but slightly different decause you have too filter out the other packets that are not ICMP(Internet Control Message Protocol). So for that go to the diplay filter and input icmp then hit enter and you should get only the ICMP packets on your screen. Now look at the status bar at the bottom there you should see how many ICMP packets were captured with parcentage.

#### Q2: There was an ICMP ping request packet, which did not receive any response back. What is the packet number?

First filter the ICMP packets then search for the packets with no response there should be written (no response found!) on the right of the packet.
<img src="/img/img8.PNG"><br>
#### Q3: What was thr source IP of the above packet?

after after you locate that package look at the third column of the the list (the third column is for the souce IP).
<img src="/img/img9.PNG"><br>
#### Q4: What was thr destination IP of the above packet?

after after you locate that package look at the fourth column of the the list (the fourth column is for the destination IP).
#### Q5: What is the length of the packet?

after after you locate that package look at the sixth column of the the list (the sixth column is for the length).
<img src="/img/img10.PNG"><br>
#### Q6: In which country standard time was the packet captured?

For this select the packet similar to [Task 2](#now-lets-get-into-task-2-in-task-2-the-first-question-is-) [Q1](#q1-when-was-the-first-packet-captured-format--year-month-date-hoursminutesseconds) look for the Arrival time and you should be able to see In which country standard time was the packet captured .
#### Q7:  When the packet was captured? (Format : Year-Month-Date Hours:Minutes:Seconds)

It's in the Arrival time too.
#### Q8: What is the data value of the packet?

Select the packet then look the the Packet Details Pane there you should see a drop-dow bar named Internet Control Message Protocol. Drop it down and you should see this :

Now drop-down the bar named Data and you should get a field name & Value. right click on it and copy the value.
<img src="/img/img11.PNG"><br>
#### Q9: Decode the value.

The value is in hex so decode it however you want. Use a tool or script. You should be able to do this much by your self.
#### Q10: In the decoded strings there was  an username and a password, what are those?

After decoding it you should get the user name and password in the decoded value.

## Task 4

#### Q1:  How many FTP packets were captured? (with parcentage)

It's same as the [Task 3](#task-3) [Q1](#q1-how-many-icmp-packets-were-captured-with-parcentage) just filter the FTP packets.

#### Q2: What was the user's first username and password that tried to login to frp server? (Format: username:password)

Use this for filter for filtering the USER packets.
```bash
ftp.request.command == "USER"
```
Use this for filter for filtering the USER packets.
```bash
ftp.request.command == "PASS"
```
#### Q3: What was the user's last username and password that tried to login to frp server? (Format: username:password)

It's same as [Task 4](#task-4) [Q2](#q2-what-was-the-users-first-username-and-password-that-tried-to-login-to-frp-server-format-usernamepassword) just figure out whuch one was the first one anjd last one by yourself.

#### Q4: What was the user's last username and password that tried to login to frp server? (Format: username:password)

Use this filter to see the packtes that where captured when dowloading the files in FTP
```bash
ftp.request.command == "RETR"
```
#### Q5: Which file is seems to be malicious? (Format: File Extension)


#### Q6: What is the MD5 hash of the malicious file? 

Okey so the malicious file CyberSec.pdf has a batch payload in it so if you download it windowsa your defender will remove it. So download it on linux and use the [MD5 encryption py script](#md5-encryption-py-script).
and don't worry windows because ["I am here"](https://github.com/ACE-UCHIHA). It took me some time but I got a website where you can analyze the pcapng file and the website also provides a tables with different infornmation about the files that are in the pcapng file like the CyberSrc.pdf, thm.png etc. anhd yes you guessed it in those information there is the MD5 hash of those files too. 
website URL: 
```url
https://lab.dynamite.ai/
```
go to the website upload the pcapng file then at the look at the left sidebar there should be a option named "Artifacts" click on that then go to the bottom of the page and you  should be able to see a table name "Interactive Data Table". In this table you'll find the MD5 hash.

#### Q7: What is the MD5 hash of the normal file? 

The normal file is thm.png to get the file you can use the methods in the [Task 4](#task-4) [Q6](#q6-what-is-the-md5-hash-of-the-malicious-file) but now you can use both methods in windows andf linux.

#### Q8: What is the file size of malicious file? (Format: In Bytes)

for this click on the malicious file look at the Packet Details Pane there you should see a row [Command response bytes: *****] . find this in the Packet Details Pane and you'll get the file size in bytes.

#### Q9: What is the file size of noraml file? (Format: In Bytes)

Same as [Task 4](#task-4) [Q8](#q8-what-is-the-file-size-of-malicious-file-format-in-bytes) .

#### Q10: In which which directory was the normal file located?


for this click on the normal file look at the Packet Details Pane there you should see a row [Current working directory: ***-***] find this in the Packet Details Pane and you'll get the file size in bytes.


#### Q11: In which which directory was the malicious file located?

This is same as the [Task 4](#task-4) [Q10](#q10-in-which-which-directory-was-the-normal-file-located) but you won't see any directory there because it was in the root directory. so there isn't any directory defined.

#### Q12: What is the IP of the device that was infected by the malicious file?

locate the malicious file then look for the destination IP . and that is the IP you were looking for.



 
