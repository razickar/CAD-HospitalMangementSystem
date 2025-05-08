# CAD-HospitalMangementSystem
Project :- Hospital Management System

Title:- Healthcare

Type:- B2B

Target audience:- [patients, doctors, nurses, hospital staff, receptionists, lab technicians]

Budget:- currently time is budget.

Members:- 1.


Features:-

	-registration
	  *patient
	  *Staff
	  *doctor
	-login for 
	  *patient
	  *Staff
	  *doctor
	-doctor appointment booking
	-doctor availability
	-digital reports
	-patient history tracking
	-medical conference with doctor (webrtc)
	-filter 
	-appointment notification
	-contact info
	-billing (different payment method())
	-admin dashboard (ellam irukum home page mari)
	-access based on user
 
Feasibility:-

	-registration
	-login
	-doctor listing and search
	-appointment booking and cancellation
	-video call conselt with doctor (Phase 2)
	-digital reports
	-payment system (Phase 2)
	-notification
	-receptionist control 
	-role-access ( still loading mind)

 
 Data Model:-

 # Registration - Class

 -- Registration for patient 
 
    -Name: String
    -DOB : String
    -phone no : long
    -PatientDiseases : String
    -userId : long(auto generate) + enum(@staff,@doctor,@pateint,@Admin)
    -password : String 
    
 -- Registration for doctor 
 
    -Name: String
    -DOB : String
    -phone no : long
    -which Specalist : String
    -userId : long(auto generate) + enum(@staff,@doctor,@pateint,@Admin)
    -password : String 


 -- Registration for staff 
 
    -Name: String
    -DOB : String
    -phone no : long
    -Staff Role : String
    -userId : long(auto generate) + enum(@staff,@doctor,@pateint,@Admin)
    -password : String 	
		
 # Login - Class
 
    -- UserId : long(auto generate) + enum(@staff,@doctor,@pateint,@Admin) this is regex for seperation
    -- Password : String

 # Appoinment / cancel  -  Class

 -Choose doctor : String
 -Choose Availabilty : long
 -Description : String
 -Cancellation *(use ing Map)
 	
