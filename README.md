# System-for-HOSPITAL-PATIENT-DATABASE
Basic c-program to create a databse of hospital patient and sorting them by bill amount in a descending order
#include <stdio.h>

struct Patient {
    int patientID;
    char name[50];
    int age;
    char gender[10];
    char disease[50];
    char doctor[50];
    float billAmount;
};

int main() {
    struct Patient patients[100], temp;
    int n, i, j;

    printf("Enter number of patients: ");
    scanf("%d", &n);

    
    for(i = 0; i < n; i++) {
        printf("\nEnter details for patient %d\n", i + 1);
        printf("Patient ID: ");
        scanf("%d", &patients[i].patientID);
        printf("Name: ");
        scanf("%s", patients[i].name);
        printf("Age: ");
        scanf("%d", &patients[i].age);
        printf("Gender: ");
        scanf("%s", patients[i].gender);
        printf("Disease: ");
        scanf("%s", patients[i].disease);
        printf("Doctor: ");
        scanf("%s", patients[i].doctor);
        printf("Bill Amount: ");
        scanf("%f", &patients[i].billAmount);
    }

    
    for(i = 0; i < n - 1; i++) {
        for(j = i + 1; j < n; j++) {
            if(patients[j].billAmount > patients[i].billAmount) {
                temp = patients[i];
                patients[i] = patients[j];
                patients[j] = temp;
            }
        }
    }

    
    printf("\n--- Patient Records (Sorted by Bill Amount Descending) ---\n");
    printf("ID\tName\tAge\tGender\tDisease\tDoctor\tBill\n");
    for(i = 0; i < n; i++) {
        printf("%d\t%s\t%d\t%s\t%s\t%s\t%f\n",
               patients[i].patientID,
               patients[i].name,
               patients[i].age,
               patients[i].gender,
               patients[i].disease,
               patients[i].doctor,
               patients[i].billAmount);
    }

    return 0;
}
