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

 ## Registration - Class

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


  Registration for staff 
 
    -Name: String
    -DOB : String
    -phone no : long
    -Staff Role : String
    -userId : long(auto generate) + enum(@staff,@doctor,@pateint,@Admin)
    -password : String 	
		
  Login - Class
 
    -- UserId : long(auto generate) + enum(@staff,@doctor,@pateint,@Admin) this is regex for seperation
    -- Password : String

  Appoinment / cancel  -  Class

	 -Choose doctor : String
	 -Choose Availabilty : long
	 -Description : String
	 -Cancellation *(use ing Map)
 	
 Doctor Listing and Search - Class

	DoctorId: Long
	Name: String
	Specialization: String
	Experience: Integer
	AvailableDays: List<String>
	AvailableTimeSlots: Map<String, List<String>>
	ConsultationFee: Double
	Rating: Float
	TotalPatients: Integer
	ProfileImage: String
	Biography: String

Appointment - Class

	AppointmentId: Long
	PatientId: Long
	DoctorId: Long
	AppointmentDate: String
	AppointmentTime: String
	Status: Enum(SCHEDULED, COMPLETED, CANCELLED, RESCHEDULED)
	BookingTime: DateTime
	Description: String
	Cancellation: Map<String, String> // Reason, CancelledBy

Video Consultation - Class (Phase 2)

	ConsultationId: Long
	AppointmentId: Long
	PatientId: Long
	DoctorId: Long
	ScheduledStartTime: DateTime
	ActualStartTime: DateTime
	EndTime: DateTime
	Status: Enum(SCHEDULED, IN_PROGRESS, COMPLETED, CANCELLED)
	RecordingUrl: String
	Notes: String

Digital Reports - Class

	ReportId: Long
	PatientId: Long
	DoctorId: Long
	AppointmentId: Long
	ReportType: String
	ReportDate: DateTime
	FileUrl: String
	Description: String
	IsSharedWithPatient: Boolean
	SharedDate: DateTime

Payment System - Class (Phase 2)

	PaymentId: Long
	AppointmentId: Long
	PatientId: Long
	Amount: Double
	PaymentMethod: Enum(CREDIT_CARD, DEBIT_CARD, UPI, NET_BANKING, INSURANCE)
	TransactionId: String
	Status: Enum(PENDING, COMPLETED, FAILED, REFUNDED)
	PaymentDate: DateTime
	RefundAmount: Double
	RefundDate: DateTime

Notification - Class

	NotificationId: Long
	UserId: Long
	UserType: Enum(@staff, @doctor, @patient, @Admin)
	Title: String
	Message: String
	CreatedAt: DateTime
	IsRead: Boolean
	Type: Enum(APPOINTMENT_REMINDER, REPORT_AVAILABLE, PAYMENT_CONFIRMATION, SYSTEM_UPDATE)

Receptionist Control - Class

	ControlId: Long
	StaffId: Long
	ActionType: Enum(BOOK_APPOINTMENT, CANCEL_APPOINTMENT, RESCHEDULE_APPOINTMENT, CHECK_IN_PATIENT, UPDATE_PATIENT_INFO)
	ActionTime: DateTime
	PatientId: Long
	AppointmentId: Long
	Notes: String
	Status: Enum(PENDING, COMPLETED, CANCELLED)

Role Access - Class

	RoleId: Long
	RoleName: Enum(@staff, @doctor, @patient, @Admin)
	Permissions: Map<String, Boolean>
 from GPT-----------------------------------------
/* Example permissions:

VIEW_PATIENT_RECORDS: Boolean
EDIT_PATIENT_RECORDS: Boolean
SCHEDULE_APPOINTMENTS: Boolean
ACCESS_FINANCIAL_DATA: Boolean
MANAGE_USERS: Boolean
VIEW_REPORTS: Boolean
GENERATE_REPORTS: Boolean
MANAGE_DOCTORS: Boolean
MANAGE_STAFF: Boolean
*/


	CreatedBy: Long
	CreatedAt: DateTime
	LastModifiedBy: Long
	LastModifiedAt: DateTime

Patient Records - Class

	PatientId: Long
	MedicalHistory: List<String>
	Allergies: List<String>
	CurrentMedications: List<String>
	PreviousAppointments: List<Long>
	UpcomingAppointments: List<Long>
	FamilyDoctorId: Long
	EmergencyContact: String
	EmergencyContactPhone: Long
	InsuranceDetails: Map<String, String>
	LastVisitDate: DateTime
