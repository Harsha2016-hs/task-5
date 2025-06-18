# task-5
# Contact Management System with Pre-filled Contacts

contacts = [
    {
        "name": "Ramesh Kumar",
        "phone": "9876543210",
        "email": "ramesh.kumar@example.com",
        "address": "123 Gandhi Street, Chennai"
    },
    {
        "name": "Sita Sharma",
        "phone": "9123456780",
        "email": "sita.sharma@example.com",
        "address": "22 Park Avenue, Mumbai"
    },
    {
        "name": "Amit Verma",
        "phone": "9988776655",
        "email": "amit.verma@example.com",
        "address": "56 Nehru Road, Delhi"
    },
    {
        "name": "Priya Das",
        "phone": "9345612789",
        "email": "priya.das@example.com",
        "address": "78 MG Road, Bengaluru"
    }
]

def add_contact():
    print("\nAdd New Contact")
    name = input("Enter full name: ")
    phone = input("Enter phone number: ")
    email = input("Enter email address: ")
    address = input("Enter full address: ")
    contact = {"name": name, "phone": phone, "email": email, "address": address}
    contacts.append(contact)
    print(f"Contact for '{name}' added successfully!")

def view_contacts():
    print("\nContact List:")
    if not contacts:
        print("No contacts available.")
    else:
        for i, contact in enumerate(contacts, start=1):
            print(f"\nContact {i}")
            print(f"Name    : {contact['name']}")
            print(f"Phone   : {contact['phone']}")
            print(f"Email   : {contact['email']}")
            print(f"Address : {contact['address']}")

def search_contact():
    print("\nSearch Contact")
    keyword = input("Enter name or phone number: ").lower()
    found = False
    for contact in contacts:
        if keyword in contact['name'].lower() or keyword in contact['phone']:
            print("\nContact Found:")
            print(f"Name    : {contact['name']}")
            print(f"Phone   : {contact['phone']}")
            print(f"Email   : {contact['email']}")
            print(f"Address : {contact['address']}")
            found = True
            break
    if not found:
        print("No contact found.")

def update_contact():
    print("\nUpdate Contact")
    phone = input("Enter the phone number of the contact to update: ")
    for contact in contacts:
        if contact['phone'] == phone:
            print(f"Updating contact: {contact['name']}")
            contact['name'] = input("New name: ")
            contact['phone'] = input("New phone: ")
            contact['email'] = input("New email: ")
            contact['address'] = input("New address: ")
            print("Contact updated successfully.")
            return
    print("Contact not found.")

def delete_contact():
    print("\nDelete Contact")
    phone = input("Enter the phone number of the contact to delete: ")
    for i, contact in enumerate(contacts):
        if contact['phone'] == phone:
            confirm = input(f"Are you sure you want to delete '{contact['name']}'? (yes/no): ")
            if confirm.lower() == 'yes':
                del contacts[i]
                print("Contact deleted.")
            else:
                print("Deletion cancelled.")
            return
    print("Contact not found.")

def main():
    while True:
        print("\n--- Contact Management Menu ---")
        print("1. Add Contact")
        print("2. View Contacts")
        print("3. Search Contact")
        print("4. Update Contact")
        print("5. Delete Contact")
        print("6. Exit")

        choice = input("Enter your choice (1–6): ")

        if choice == '1':
            add_contact()
        elif choice == '2':
            view_contacts()
        elif choice == '3':
            search_contact()
        elif choice == '4':
            update_contact()
        elif choice == '5':
            delete_contact()
        elif choice == '6':
            print("Exiting... Goodbye!")
            break
        else:
            print("Invalid choice. Please choose between 1–6.")

# Run the program
main()
