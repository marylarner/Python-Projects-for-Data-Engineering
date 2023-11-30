# Install a Package with the pip Command

## Instructions:

**1. Type:** 
```
source setup-env.sh
```
To set up an empty environment.

**2. Type:** 
```
pip help
``` 
To see the documentation for pip. 

**3. Type:** 
```
pip help install
``` 
To see the help for the pip install command. 

**4. Install the requests package:** 
```
pip install requests
``` 

**5. See the packages installed in your environment:** 
```
pip list
``` 

**6. To see the available versions of the `requests` package:** 
```
pip install requests==
```  
**Note:** this will give an error message, but in that message all the available versions are displayed. 

**7. Choose an earlier version of requests and install that version:** 
```
pip install requests==2.25.1 
```

**8. Check the installed version:** 
```
pip list
```

**9. Upgrade to the latest version:** 
```
pip install requests --upgrade
``` 

**10. Check the installed version:** 
```
pip list
```