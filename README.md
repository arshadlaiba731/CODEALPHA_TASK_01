# Internship_Tasks_Submission
Repository For Codealpha Internship Projects 

#include <iostream>
#include <iomanip> // for std::setprecision

using namespace std;

// Function to calculate the GPA for the semester
double calculateGPA(double gradePoints[], int credits[], int numCourses) {
    double totalGradePoints = 0;
    int totalCredits = 0;

    for (int i = 0; i < numCourses; ++i) {
        totalGradePoints += gradePoints[i] * credits[i];
        totalCredits += credits[i];
    }

    if (totalCredits == 0) return 0; // To avoid division by zero

    return totalGradePoints / totalCredits;
}

// Function to calculate CGPA based on all semesters' GPAs
double calculateCGPA(double gpas[], int creditsPerSemester[], int numSemesters) {
    double totalGradePoints = 0;
    int totalCredits = 0;

    for (int i = 0; i < numSemesters; ++i) {
        totalGradePoints += gpas[i] * creditsPerSemester[i];
        totalCredits += creditsPerSemester[i];
    }

    if (totalCredits == 0) return 0; // To avoid division by zero

    return totalGradePoints / totalCredits;
}

int main() {
    int numCourses;
    cout << "Hello! Welcome to the CGPA Calculator.\n";
    cout << "First, let's enter the details for your courses this semester.\n";
    cout << "How many courses did you have? ";
    cin >> numCourses;

    // Use arrays instead of vectors
    double gradePoints[numCourses];
    int credits[numCourses];

    cout << "\nPlease provide the following details for each course:\n";
    for (int i = 0; i < numCourses; ++i) {
        cout << "For Course " << i + 1 << ",\n";
        cout << "  How many credits was it worth? ";
        cin >> credits[i];
        cout << "  What grade points did you earn? ";
        cin >> gradePoints[i];
    }

    double gpa = calculateGPA(gradePoints, credits, numCourses);

    cout << fixed << setprecision(2);
    cout << "\nYour GPA for this semester is: " << gpa << endl;

    int numSemesters;
    cout << "\nNow, let's figure out your overall CGPA.\n";
    cout << "How many semesters have you completed so far? ";
    cin >> numSemesters;

    // Use arrays instead of vectors
    double gpas[numSemesters];
    int creditsPerSemester[numSemesters];

    for (int i = 0; i < numSemesters; ++i) {
        cout << "\nFor Semester " << i + 1 << ",\n";
        cout << "  What was your GPA? ";
        cin >> gpas[i];
        cout << "  How many credits did you complete? ";
        cin >> creditsPerSemester[i];
    }

    double cgpa = calculateCGPA(gpas, creditsPerSemester, numSemesters);

    cout << "\nYour Cumulative GPA (CGPA) is: " << cgpa << endl;
    cout << "Great job! You've finished your calculations.\n";
    cout << "Thanks for using the CGPA Calculator. Have a wonderful day!" << endl;

    return 0;
}
