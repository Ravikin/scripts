from selenium import webdriver

from time import sleep

  

END = 14

URL = "http://localhost:3000/#/"

  

driver = webdriver.Chrome()

  
  

for i in range(1,END+1):

    driver.maximize_window()

    driver.get(URL+str(i))

    sleep(0.6)

    driver.save_screenshot(str(i)+'.png')

  
  

driver.quit()