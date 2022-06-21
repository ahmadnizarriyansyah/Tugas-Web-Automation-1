*** Settings ***
Library                         SeleniumLibrary
Test Setup                      Open Browser                                  ${base_url}               ${browser_type}
Test Teardown                   Close Browser

*** Variable ***
${base_url}                     https://pub-eish-dev.keponet.com/
${browser_type}                 gc
${email_user}                   jenarishsatu@yopmail.com
${password_user}                123456789

*** Test Cases ***
I am Login with valid Email and invalid Password
    Maximize Browser Window
    Input Text                           //input[@id="email"]                   ${email_user}
    Input Text                           //input[@id="password"]               ${password_user}
    Click Element                        //button[@type="submit"]                 
    Wait Until Element Is Not Visible    //div[@class="alert alert-danger text-danger"]
    Element Should Not Be Visible        //div[@class="alert alert-danger text-danger"]
