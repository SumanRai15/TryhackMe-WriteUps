<h1>TRY HACK ME WriteUp</h1>
<h2>Wonderland</h2>
<h3>Difficulty: Medium</h3>

<p>This lab requires basic enumeration skill, directory bruteforcing, privilege escalation technique.</p>
<p><b>This is the default homepage of Wonderland website</b></p>
<div align="center">
<a href="images/01.png">
 <img src="images/01.png" width="1600"/>
</a>
  
**Figure 1:** Wonderland Homepage.

</div>
<p>I run nmap scan but nothing interesting port was found to be open, so i moved on with basic directory bruteforcing using <b>gobuster</b></p>

<div align="center">
<a href="images/02.png">
 <img src="images/02.png" width="1600"/>
</a>
  
**Figure 2:** found one interesting directory <b>r</b>.

</div>

<p>Again nothing interesting was found in the <b>r</b> directory. So i again used <b>gobuster</b> to further enumerate directory</p>
<div align="center">
<a href="images/03.png">
 <img src="images/03.png" width="1600"/>
</a>
  
**Figure 3:** Found another directory inside <b>r</b>.

</div>

<p>I repeated the process using <b>gobuster</b> and finally found something interesing.</p>
<div align="center">
<a href="images/05.png">
 <img src="images/05.png" width="1600"/>
</a>
  
**Figure 4:** Directory /r/a/b/b/i/t.

</div>
<p>This is the webpage for directory /r/a/b/b/i/t</p>
<p>Upon viewing its page source we can see the credentials for alice user</p>

<div align="center">
<a href="images/06.png">
 <img src="images/06.png" width="1600"/>
</a>
  
**Figure 5:** Found <b>alice</a> credentials.

</div>

<p>Now next step is to try log into ssh using alice creds</p>

<div align="center">
<a href="images/07.png">
 <img src="images/07.png" width="1600"/>
</a>
  
**Figure 6:** Logged In as alice.

</div>

<p>I viewed every files and folders, but user.txt was nowhere to be found so I just though maybe we can find user.txt file inside root folder and I was absolutely right</p>

<div align="center">
<a href="images/08.png">
 <img src="images/08.png" width="1600"/>
</a>
  
**Figure 7:** Found user.txt.

</div>

<p>Now its time for Privilege Escalation. The first command that I always use for privilege escalation is <b>sudo -l</b></p>
<p>Below image shows that we can actually use sudo as rabbit user which is really a good starting point for us.</p>

<div align="center">
<a href="images/11.png">
 <img src="images/11.png" width="1600"/>
</a>
  
**Figure 8:** .

</div>

<p>Next, I found python file which is using random library upon its execution. So we need to create a new file and name it random.py and add our payload inside it.</p>

<div align="center">
<a href="images/09.png">
 <img src="images/09.png" width="1600"/>
</a>
  
**Figure 9:** Inspecting python file inside alice folder.

</div>

<div align="center">
<a href="images/12.png">
 <img src="images/12.png" width="1600"/>
</a>
  
**Figure 10:**

</div>

<div align="center">
<a href="images/13.png">
 <img src="images/13.png" width="1600"/>
</a>
  
**Figure 11:** LoggedIn as rabbit user

</div>





