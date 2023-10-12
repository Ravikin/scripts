---
theme: ravi
---
## Automate 
### web screenshots with Python
![[Untitled-1.png]]

---
## Automate <br>
### web screenshots with Python
![[Untitled-1 1.png]]

notes: 
i was preparing to make a video about code blocks in motion canvas and I reached the stage where I make screenshots of slides from advanced slides plugin in Obsidian

---

![[Pasted image 20231011145813.png]]

notes:
to create a video I make a screenshot of each slide and then record voice and add clip on top of it

---

![[Pasted image 20231011145916.png]]

notes:
there were 35 slides to capture as there is no option in Obsidian to export as anything other than PDF which does not change anything

---

![[Pasted image 20231011150022.png]]

notes: 
So I did what every IT person does...."how to make screenshot with python"

---

PySide or PyQt4 does not work on anything newer than<br>
![[Pasted image 20231011150052.png]]
from 2019

notes: 
I will spare you dozen minutes of searching for modern solution as most responses to my problem were out of date or bulky to say at least

---

![[Pasted image 20231011150318.png]]

notes: 
Finally I found my savior which was even older but selenium library is still developed and solution was easiest. So I fired up VSCode and did a thing

---

![[000002.png]]

notes:
This was my code.

---

![[python-screengrabber.mp4]]

notes:
To simplify things just a little bit I created Two variables for max slide count (highlight END) and address (highlight URL) in case i would need it. 

---

![[python-screengrabber.mp4]] 

notes:  (for loop highlighted)
Then for each slide I tell selenium to open URL (driver.get(URL+str(i))) for correct one, wait because advanced slides have slide transition (sleep(0.6)) and grab a screenshot    () driver.save_screenshot(str(i)+'.png') . Also to make them big and simple copy and paste I maximize window. 

---

![[python-screengrabber.mp4]] 

notes:
After that we are left with closing our browser 

---

![[Pasted image 20231011152145.png]]

notes:
and can go to folder with screenshots. It will be the directory you run script from. You can obviously specify that in  


---

```python
            driver.save_screenshot(str(i)+'.png')
```

notes:
this part and provide whole path but I'm lazy and it's easier to run it from correct place. Or do it multiple times if you forgot. :D 

---

![[cropped-cyber_frog_mpiorkowski_icon-1-200x200.png]]
MPIORKOWSKI.COM
# Thank You!

notes:
That was all from my side. Thank you for your attention and have a great rest of your day!


---

clip with no sleep 