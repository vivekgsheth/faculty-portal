# Faculty-portal"# faculty-portal" 
Challenges:
ONE-TO-ONE Chat module:
Problem with maintaining open web-socket connection, due to version issue, so we moved to using REST api , so used Django Rest Framework(DRF).
MOdal forms:
Whenever a new obj was created for qualification, we required a reference for faculty. We did that by overriding the get_form_kwargs of BSModal, fetched the  faculty id from url and passed it to form. In form, we override the __init__ method of MODALFORM. We retrieved the faculty object using the facukty id, and initialized the faculty field using this faculty object. Now, to hide the faculty id in form, we used widget and hid the id label and input.
AUTO FACULTY ID GENERATION:
Generally, when admin registers a faculty, the data is saved using save_model method. Now, to autogenerate and insert faculty id, we overrid the save_modal method of model_admin class. We used current year, details saved in obj for department and count from number of faulties in departmentand initialized the obj.facultyid and called super().
OTP:
OTP generation using twilio.

Limitaions:
In CHAT MODULE, user cannot see the online status and read status for another user.
The receive method is called every second from backend. It puts additional overhead on system. This can be overcome by using web-sockets but websocket had its own limitaion.

Explanation:
When a user wants to use the system, admin adds his details, and with the autogenerated faculty id, faculties use this id to generate paswrod using OTP as a first time user, there after, he can add/edit detials including qualifications, teaching interests, experience certifications and specializations. Faculty can also add to-dos and view today's to-do's in the page. Also, one can chat with other faculties using chat module.
