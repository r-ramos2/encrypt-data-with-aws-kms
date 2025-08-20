<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Encrypt Data with AWS KMS

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-kms)

**Author:** R  


---

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/aws-security-kms_w0x1y2z3)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use AWS KMS to encrypt a DynamoDB database. The goal is to protect data from unauthorized access while allowing authorized users to securely store and retrieve information.

### Tools and concepts

Services I used include AWS KMS, DynamoDB, and IAM. Key concepts I learnt include encryption, key policies, access control, and transparent data encryption. I also gained experience in creating customer-managed keys, applying them to data services, and verifying access control using IAM users.

### Project reflection

This project took me approximately 1 hour. The most challenging part was configuring and validating the key policy to grant secure yet limited access. It was most rewarding to see encryption enforced in real-time and understand how AWS secures data through fine-grained permissions.

I did this project to deepen my understanding of AWS security and encryption services. Yes, the project met my goals by providing hands-on practice with KMS, data encryption in DynamoDB, and IAM-based access control.

---

## Encryption and KMS

Encryption is the process of converting readable data into ciphertext using algorithms. Companies and developers do this to protect sensitive information. Encryption keys are the codes that guide how data is scrambled and later decrypted.

AWS KMS is a managed service that lets you create and control encryption keys. Key management systems are important because they secure keys, manage access, and provide auditing to meet data protection and compliance needs.

Encryption keys are broadly categorized as symmetric or asymmetric. I set up a symmetric key because it uses a single key for both encryption and decryption, making it faster and more efficient for securing large volumes of data like in DynamoDB.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/aws-security-kms_a2b3c4d5)

---

## Encrypting Data

My encryption key will safeguard data in DynamoDB, which is a fast, fully managed NoSQL database service designed for high-performance applications that need quick, scalable access to large volumes of data.

The different encryption options in DynamoDB include Amazon-owned keys, AWS managed keys, and customer managed keys. Their differences are based on control and visibility. I selected a customer managed key for full control and enhanced security.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/aws-security-kms_q8r9s0t1)

---

## Data Visibility

Rather than controlling who has access to the key, KMS manages user permissions by enforcing granular policies that define who can use the key for actions like encrypting, decrypting, or generating data keys. Only users explicitly granted these permissions can operate on encrypted resources.

Despite encrypting my DynamoDB table, I could still see the table's items because I have permission to use the KMS key. DynamoDB uses transparent data encryption, which means it decrypts data for authorized users automatically.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/aws-security-kms_c0d1e2f3)

---

## Denying Access

I configured a new IAM user to test restricted access to encrypted data. The permission policies I granted this user are AmazonDynamoDBFullAccess, but not access to the KMS key used for encryption.

After accessing the DynamoDB table as the test user, I encountered an “Access denied” error because the user lacked permissions to decrypt data with the KMS key. This confirmed that even with full DynamoDB access, users cannot view encrypted data without explicit KMS key permissions.

![Image](http://learn.nextwork.org/serene_teal_majestic_duck/uploads/aws-security-kms_w0x1y2z3)

---

## EXTRA: Granting Access

---

---
