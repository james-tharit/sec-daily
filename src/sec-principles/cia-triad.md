# CIA Triad

The CIA triad is a **model** that helps inform how we consider risk when setting up system and security policies.

![CIA Triad](./images/cia-traid.png)

CIA are the three foundational principles used by cybersecurity professionals to establish appropriate controls that mitigate threats, risks, and vulnerabilities.

## Confidentiality

Confidentiality is the idea that only authorized users can access specific assets or data. Confidentiality can be enhanced through the implementation of design, such as the [principle of least privilege](../sec-principles/least-privilege.md).

## Integrity

Integrity is the idea that the data is verifiably correct, authentic, and reliable. Having protocols in place to verify the authenticity of data is essential. One way to verify data integrity is through cryptography, which is used to transform data so unauthorized parties cannot read or tamper with it (NIST, 2022). Another example of how an organization might implement integrity is by enabling encryption, which is the process of converting data from a readable format to an encoded format. It can be used to prevent access to data, such as messages on an organization's internal chat platform.

## Availability

Availability is the idea that data is accessible to those who are authorized to use it. When a system adheres to both availability and confidentiality principles, data can be used when needed. In the workplace, this could mean that the organization allows remote employees to access its internal network to perform their jobs. It’s worth noting that access to data on the internal network is still limited, depending on what type of access employees need to do their jobs.

For example, an employee works in the organization’s accounting department, they might need access to corporate accounts but not data related to ongoing development projects.
