# ADVANCED-ENCRYPTION-TOOL
COMPANY: CODETECH IT SOLUTIONS

NAME: ANISHA PRAVIN

INTERN ID: CITSOD165

DOMAIN: CYBERSECURITY

DURATION: 4 WEEKS

MENTOR: NEELA SANTHOSH

DESCRIPTION

 What This Tool Does
This tool lets you:

Generate a secure key for encryption

Encrypt a secret message (like a password or note)

Decrypt the message back to normal

Do everything through a simple menu

It uses AES encryption under the hood (via a module called Fernet in the cryptography library). AES is one of the most secure and commonly used encryption methods.

 What Each Part of the Code Does
 1. Generate Key
python
Copy
Edit
def generate_key():
    key = Fernet.generate_key()
    with open("secret.key", "wb") as key_file:
        key_file.write(key)
 This creates a random secret key (like a password) and saves it to a file named secret.key.

📁 This file is needed every time you encrypt or decrypt something.

 2. Load Key
def load_key():
    return open("secret.key", "rb").read()
This reads the key from the secret.key file.

 You need the same key to decrypt anything you’ve encrypted earlier.

 3. Encrypt Message

def encrypt_message(message):
    key = load_key()
    fernet = Fernet(key)
    encrypted = fernet.encrypt(message.encode())
    return encrypted
 This:

Converts your message (like "hello") into encrypted gibberish (like "gAAAAA...")

Uses the key to lock the message

 Example:

vbnet

Input: hello
Output: gAAAAABlZG89Lm... (Encrypted string)
 4. Decrypt Message

def decrypt_message(encrypted_message):
    key = load_key()
    fernet = Fernet(key)
    decrypted = fernet.decrypt(encrypted_message).decode()
    return decrypted
 This:

Takes the encrypted string and your key

Unlocks it and gives back the original message

 5. Main Menu

def main():
    while True:
        print("1. Generate New Key")
        print("2. Encrypt Message")
        print("3. Decrypt Message")
        print("4. Exit")
This lets you interact with the tool:

Press 1 to create a new key

Press 2 to encrypt text

Press 3 to decrypt encrypted text

Press 4 to exit the program

 Simple Example
1. Generate New Key
→ This creates a secret.key file

2. Encrypt Message
→ You enter: "secret123"
→ You get: gAAAAABi...

3. Decrypt Message
→ You paste: gAAAAABi...
→ It gives back: secret123
 This proves the encryption and decryption works properly!

 Why This Is Secure
Uses AES encryption via Fernet

Automatically handles things like:

Key size

Initialization vector (IV)

Integrity checking (detects tampering)

You don’t need to worry about technical math—it’s already handled securely!

 Summary
Feature	Purpose
Generate Key	Creates and saves secret key
Encrypt Text	Locks a message using the key
Decrypt Text	Unlocks it with the same key
Menu System	Makes it user-friendly to operate

from cryptography.fernet import Fernet

# --- Generate Key and Save It ---
def generate_key():
    key = Fernet.generate_key()
    with open("secret.key", "wb") as key_file:
        key_file.write(key)
    print("[+] Key generated and saved as secret.key")

# --- Load the Key from File ---
def load_key():
    return open("secret.key", "rb").read()

# --- Encrypt Message ---
def encrypt_message(message):
    key = load_key()
    fernet = Fernet(key)
    encrypted = fernet.encrypt(message.encode())
    return encrypted

# --- Decrypt Message ---
def decrypt_message(encrypted_message):
    key = load_key()
    fernet = Fernet(key)
    decrypted = fernet.decrypt(encrypted_message).decode()
    return decrypted

# --- Main Menu ---
def main():
    while True:
        print("\n--- Advanced Encryption Tool ---")
        print("1. Generate New Key")
        print("2. Encrypt Message")
        print("3. Decrypt Message")
        print("4. Exit")

        choice = input("Choose an option: ")

        if choice == '1':
            generate_key()
        elif choice == '2':
            msg = input("Enter message to encrypt: ")
            encrypted = encrypt_message(msg)
            print(f"[+] Encrypted: {encrypted.decode()}")
        elif choice == '3':
            enc_msg = input("Enter encrypted message: ").encode()
            try:
                decrypted = decrypt_message(enc_msg)
                print(f"[+] Decrypted: {decrypted}")
            except:
                print("[-] Error: Invalid key or message")
        elif choice == '4':
            break
        else:
            print("Invalid choice")

if __name__ == "__main__":
    main()

OUTPUT
<img width="627" height="596" alt="Image" src="https://github.com/user-attachments/assets/77d33012-1069-4d4c-8466-1bf1d2bef167" />


