from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import cv2
import keyboard
import base64

driver = webdriver.Chrome('chromedriver.exe')
driver.get("https://www.google.com/")
inp = driver.find_element_by_xpath('/html/body/div[1]/div[3]/form/div[1]/div[1]/div[1]/div/div[2]/input')
inp.send_keys('protosem')
inp.send_keys(Keys.ENTER)
inp = driver.find_element_by_xpath('//*[@id="hdtb-msb"]/div[1]/div/div[4]/a').click()

for i in range(20):
    img = driver.find_element_by_xpath('//*[@id="islrg"]/div[1]/div[{}]/a[1]/div[1]/img'.format(i+1))
    #print(img.get_attribute('src'))
    imgdata = base64.b64decode(img.get_attribute('src').split(',')[1])
    filename = 'Output/{}.jpg'.format(i+1)  
    with open(filename, 'wb') as f:
        f.write(imgdata)
pos = 1
max = 20
while True:
    if keyboard.is_pressed('esc'):
        break
    elif keyboard.is_pressed('right'):
        if pos<20:
            pos=pos+1
        else:
            pos=1
    elif keyboard.is_pressed('left'):
        if pos>0:
            pos=pos-1
        else:
            pos=20 
    im = cv2.imread('Output/{}.jpg'.format(pos),cv2.IMREAD_ANYCOLOR)
    cv2.imshow(str(pos),im)
    cv2.waitKey(0)
    cv2.destroyAllWindows()
