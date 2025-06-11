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

 Registration.java
- name: String
- dob: String
- phoneNo: long
- additionalInfo: String (PatientDiseases/Specialization/StaffRole)
- userId: long (auto-generated + enum prefix)
- password: String
- userRole: UserRole
Login.java
- userId: long (with enum prefix for role separation)
- password: String
- userRole: UserRole (extracted from userId regex)
DoctorListing.java
- doctorId: Long
- name: String
- specialization: String
- experience: Integer
- availableDays: List<String>
- availableTimeSlots: Map<String, List<String>>
- consultationFee: Double
- rating: Float
- totalPatients: Integer
- profileImage: String
- biography: String
Appointment.java
- appointmentId: Long
- patientId: Long
- doctorId: Long
- appointmentDate: String
- appointmentTime: String
- status: AppointmentStatus
- bookingTime: DateTime
- description: String
- cancellation: Map<String, String> (Reason, CancelledBy)
VideoConsultation.java (Phase 2)
- consultationId: Long
- appointmentId: Long
- patientId: Long
- doctorId: Long
- scheduledStartTime: DateTime
- actualStartTime: DateTime
- endTime: DateTime
- status: Enum(SCHEDULED, IN_PROGRESS, COMPLETED, CANCELLED)
- recordingUrl: String
- notes: String
DigitalReport.java
- reportId: Long
- patientId: Long
- doctorId: Long
- appointmentId: Long
- reportType: String
- reportDate: DateTime
- fileUrl: String
- description: String
- isSharedWithPatient: Boolean
- sharedDate: DateTime
PaymentSystem.java (Phase 2)
- paymentId: Long
- appointmentId: Long
- patientId: Long
- amount: Double
- paymentMethod: Enum(CREDIT_CARD, DEBIT_CARD, UPI, NET_BANKING, INSURANCE)
- transactionId: String
- status: Enum(PENDING, COMPLETED, FAILED, REFUNDED)
- paymentDate: DateTime
- refundAmount: Double
- refundDate: DateTime
Notification.java
- notificationId: Long
- userId: Long
- userType: Enum(@staff, @doctor, @patient, @Admin)
- title: String
- message: String
- createdAt: DateTime
- isRead: Boolean
- type: Enum(APPOINTMENT_REMINDER, REPORT_AVAILABLE, PAYMENT_CONFIRMATION, SYSTEM_UPDATE)
ReceptionistControl.java
- controlId: Long
- staffId: Long
- actionType: Enum(BOOK_APPOINTMENT, CANCEL_APPOINTMENT, RESCHEDULE_APPOINTMENT, CHECK_IN_PATIENT, UPDATE_PATIENT_INFO)
- actionTime: DateTime
- patientId: Long
- appointmentId: Long
- notes: String
- status: Enum(PENDING, COMPLETED, CANCELLED)
RoleAccess.java
- roleId: Long
- roleName: Enum(@staff, @doctor, @patient, @Admin)
- permissions: Map<String, Boolean>
- createdBy: Long
- createdAt: DateTime
- lastModifiedBy: Long
- lastModifiedAt: DateTime
PatientRecords.java
- patientId: Long
- medicalHistory: List<String>
- allergies: List<String>
- currentMedications: List<String>
- previousAppointments: List<Long>
- upcomingAppointments: List<Long>
- familyDoctorId: Long
- emergencyContact: String
- emergencyContactPhone: Long
- insuranceDetails: Map<String, String>
- lastVisitDate: DateTime
User ID Generation Pattern:
@patient123456 - Patient ID
@doctor789012 - Doctor ID
@staff345678 - Staff ID
@admin901234 - Admin ID
Role-Based Access Flow:
Patient Flow:
Login → Patient Dashboard → Search/Filter Doctors → Book Appointments → View Digital Reports → View Medical History → Receive Notifications
Doctor Flow:
Login → Doctor Dashboard → View Scheduled Patients → Generate Digital Reports → Prescribe Medicine → Manage Availability → View Patient Records
Admin/Receptionist Flow:
Login → Admin/Receptionist Dashboard → Register New Users → Manage Appointments → Control System Settings → Manage Role-Based Access → View System Reports
Console Menu Structure:
=== Hospital Management System ===
1. Login
2. Exit
After Login:
- Patient Menu: Search Doctors → Book Appointment → View Reports → Medical History
- Doctor Menu: View Patients → Generate Reports → Prescribe Medicine → Manage Schedule  
- Admin Menu: Register Users → Manage System → Role Management → Reports
- Receptionist Menu: Patient Management → Appointment Management → Check-in Patients
