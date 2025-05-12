START FUNCTION 
‎ DISPLAY "Welcome to Donify!! The Digital Donation Platform Contribute to Causes. Make a Difference. Together." 
‎ LOOP 
‎ ‎ PROMPT "[Login / Signup]" IF user selects "Signup" THEN 
‎ CALL Signup function 
‎ ELSE IF user selects "Login" THEN 
‎ CALL Login function 
‎ ELSE 
‎ DISPLAY "Invalid option. Please try again." 
‎ END LOOP 

‎SIGNUP FUNCTION 
‎ DISPLAY "Signup" 
‎ PROMPT for name, email, password, and account type 
‎ CREATE new user object with input details 
‎ ADD new user to users list 
‎ DISPLAY "Registration successful!" 
‎ RETURN new user 
‎ 
‎LOGIN FUNCTION  
‎ DISPLAY "Login" 
‎ LOOP UNTIL valid login OR user exits 
‎ PROMPT for email and password 
‎ CHECK if user exists in users list 
‎ IF valid credentials THEN 
‎ DISPLAY "Welcome back, [user's name]!" 
‎ RETURN user 
‎ ELSE 
‎ DISPLAY "Invalid credentials. Please try again." 
‎ END LOOP 
‎ 
‎MAIN MENU FUNCTION 
‎ LOOP 
‎ DISPLAY option menu 
‎ 1. Donate Monetary 
‎ 2. Donate Items 
‎ 3. Manage Payment Methods 
‎ 4. Create Cause (Admins/Organizations only) 
‎ 5. Create Item Request (Admins/Organizations only) 
‎ 6. Logout 

PROMPT for choice  
‎ IF choice IS "1" THEN 
‎ CALL Donate Monetary function 
‎ ELSE IF choice IS "2" THEN 
‎ CALL Donate Items function 
‎ ELSE IF choice IS "3" THEN 
‎ CALL Manage Payment Methods function 
‎ ELSE IF choice IS "4" AND user IS admin/organization THEN 
‎ CALL Create Cause function 
‎ ELSE IF choice IS "5" AND user IS admin/organization THEN 
‎ CALL Create Item Request function 
‎ ELSE IF choice IS "6" THEN 
‎ DISPLAY "Logged out successfully." 
‎ BREAK 
‎ ELSE 
‎ DISPLAY "Invalid option. Please try again." 
‎ END LOOP 

‎DONATE MONETARY FUNCTION  
‎ DISPLAY available monetary cause 
‎ PROMPT user to select a cause and enter donation amount 
‎ IF valid amount THEN 
‎ CALL Process Payment function 
‎ IF payment successful THEN 
‎ UPDATE the selected cause's raised amount 
‎ DISPLAY "Thank you for your donation!" 
‎ ELSE 
‎ DISPLAY "Invalid amount or payment failed." 
‎ 
‎DONATE ITEMS FUNCTION 
‎ DISPLAY available item donation requests 
‎ PROMPT user to select a request 
‎ IF request is "Clothing Drive" THEN 
‎ CALL Donate Clothing function 
‎ ELSE 

PROMPT for quantity to donate 
‎ IF valid quantity THEN 
‎ UPDATE the selected item's received amount 
‎ DISPLAY "Thank you for your donation!" 
‎ ELSE 
‎ DISPLAY "Invalid quantity." 
‎ 
‎MANAGE PAYMENT METHODS FUNCTION 
‎ LOOP 
‎ DISPLAY payment methods menu 
‎ PROMPT user for choice 
‎ IF choice IS "1" THEN 
‎ DISPLAY user's saved payment methods 
‎ ELSE IF choice IS "2" THEN 
‎ PROMPT user to select a payment method and enter details 
‎ ADD method to user's payment_methods 
‎ DISPLAY "Payment method added." 
‎ ELSE IF choice IS "3" THEN 
‎ PROMPT user to select a payment method to remove 
‎ REMOVE selected method from user's payment_methods 
‎ DISPLAY "Payment method removed." 
‎ ELSE IF choice IS "4" THEN 
‎ BREAK 
‎ ELSE 
‎ DISPLAY "Invalid option. Please try again." 
‎ END LOOP 

‎CREATE CAUSE FUNCTION 
‎ IF user is not admin/organization THEN 
‎ DISPLAY "Permission denied." 
‎ ELSE 
‎ PROMPT for cause details (name, description, target amount) 
‎ CREATE new cause object and add to causes list 
‎ DISPLAY "Cause created successfully!" 
‎ 
‎CREATE ITEM REQUEST FUNCTION 
‎ IF user is not admin/organization THEN 
‎ DISPLAY "Permission denied." 
‎ ELSE 
‎ PROMPT for item request details (name, description, item type, quantity) 
‎ CREATE new item request object and add to item_donations list 
‎ DISPLAY "Item request created successfully!" 
‎ 
‎PROCESS PAYMENT FUNCTION 
‎ 
‎ IF user has no payment methods THEN 
‎ DISPLAY "No payment methods found." 
‎ CALL Manage Payment Methods function 
‎ RETURN FALSE 
‎ DISPLAY available payment methods 
‎ PROMPT user to select a method 
‎ IF valid selection THEN 
‎ DISPLAY "Processing payment..." 
‎ RETURN TRUE 
‎ ELSE 
‎ DISPLAY "Invalid selection." 
‎ RETURN FALSE 
‎ 
‎CALL Main Menu function for logged-in user 
‎LOOP 
‎PROMPT "Would you like to login again? (yes/no)" 
‎IF response IS "no" THEN 
‎ BREAK 
‎END LOOP 
‎ 
‎DISPLAY "Thank you for using Donify! Have a great day!"
