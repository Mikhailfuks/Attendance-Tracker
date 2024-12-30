class AttendanceTracker:
    def __init__(self):
        self.attendance_records = {}

    def mark_attendance(self, student_name, date, status):
        # If the student is not in the records, add them
        if student_name not in self.attendance_records:
            self.attendance_records[student_name] = {}

        # Mark the attendance status for the given date
        self.attendance_records[student_name][date] = status
        print(f"Attendance for {student_name} on {date} marked as {status}.")

    def view_attendance(self, student_name):
        if student_name in self.attendance_records:
            print(f"Attendance records for {student_name}:")
            for date, status in self.attendance_records[student_name].items():
                print(f"{date}: {status}")
        else:
            print(f"No attendance records found for {student_name}.")

    def view_all_attendance(self):
        if not self.attendance_records:
            print("No attendance records available.")
            return

        for student_name, records in self.attendance_records.items():
            print(f"Attendance records for {student_name}:")
            for date, status in records.items():
                print(f"{date}: {status}")
            print()

def main():
    tracker = AttendanceTracker()

    while True:
        print("\\nAttendance Tracker")
        print("1. Mark Attendance")
        print("2. View Attendance for a Student")
        print("3. View All Attendance Records")
        print("4. Exit")

        choice = input("Select an option: ")

        if choice == '1':
            student_name = input("Enter student name: ")
            date = input("Enter date (YYYY-MM-DD): ")
            status = input("Enter attendance status (Present/Absent): ")
            tracker.mark_attendance(student_name, date, status)

        elif choice == '2':
            student_name = input("Enter student name: ")
            tracker.view_attendance(student_name)

        elif choice == '3':
            tracker.view_all_attendance()

        elif choice == '4':
            print("Exiting the Attendance Tracker.")
            break

        else:
            print("Invalid option. Please try again.")

if __name__ == "__main__":
    main()
