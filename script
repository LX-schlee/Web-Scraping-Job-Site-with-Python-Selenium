from selenium import webdriver
import time
from selenium.webdriver.support.select import Select

with open('job_scraping_multipe_pages.csv', 'w') as file:
    file.write("Job_title; Location; Salary; Contract_type; Job_description \n")
    

driver=webdriver.Chrome(executable_path='C:\webdrivers\chromedriver.exe')

driver.get('https://www.jobsite.co.uk/')

driver.maximize_window()
time.sleep(1)

cookie= driver.find_element_by_xpath('//button[@class="accept-button-new"]')
try:
    cookie.click()
except:
    pass 

job_title=driver.find_element_by_id('keywords')
job_title.click()
job_title.send_keys('Software Engineer')
time.sleep(1)

location=driver.find_element_by_id('location')
location.click()
location.send_keys('Manchester')
time.sleep(1)

dropdown=driver.find_element_by_id('Radius')
radius=Select(dropdown)
radius.select_by_visible_text('30 miles')
time.sleep(1)

search=driver.find_element_by_xpath('//input[@value="Search"]')
search.click()
time.sleep(2)

for k in range(3):
    titles=driver.find_elements_by_xpath('//div[@class="job-title"]/a/h2')
    location=driver.find_elements_by_xpath('//li[@class="location"]/span')
    salary=driver.find_elements_by_xpath('//li[@title="salary"]')
    contract_type=driver.find_elements_by_xpath('//li[@class="job-type"]/span')
    job_details=driver.find_elements_by_xpath('//div[@title="job details"]/p')

    with open('job_scraping_multipe_pages.csv', 'a') as file:
        for i in range(len(titles)):
            file.write(titles[i].text + ";" + location[i].text + ";" + salary[i].text + ";" + contract_type[i].text + ";"+
                      job_details[i].text + "\n")

        next=driver.find_element_by_xpath('//a[@aria-label="Next"]')
        next.click()
    file.close()
driver.close()
