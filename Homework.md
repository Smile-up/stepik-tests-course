from selenium import webdriver
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.common.by import By
from math import*
import pyperclip



def calc(x):
    return str(log(abs(12*sin(int(x)))))


link = 'http://suninjuly.github.io/explicit_wait2.html'
browser = webdriver.Chrome('/home/smile/chrom/chromedriver')
browser.get(link)
button = WebDriverWait(browser, 12).until(EC.text_to_be_present_in_element((By.ID, "price"), '$100'))
btn = browser.find_element(By.ID, "book")
if button is True:
    btn.click()
find_x = browser.find_element_by_id('input_value')
num_x = find_x.text
pole = browser.find_element_by_id('answer')
pole.send_keys(calc(num_x))
subm = browser.find_element_by_id("solve")
subm.click()

alert = browser.switch_to.alert
alert_text = alert.text
addToClipBoard = alert_text.split(':')[-1]
pyperclip.copy(addToClipBoard)

# alert_text = browser.switch_to.alert.text.split(': ')[-1]
# alert = browser.switch_to.alert.accept()
