# Lab: Basic clickjacking with CSRF token protection

**Official PortSwigger URL:** https://portswigger.net/web-security/clickjacking/lab-basic-csrf-protected

## Lab idea

This challenge centers on an account-deletion control that uses a CSRF token. Its concept is to show that a valid token does not by itself prevent a user from being misled into activating an action on a framed page. It practices recognizing the difference between CSRF and clickjacking and assessing how interface layering can affect an authorized, signed-in user's actions.

## Vulnerability in brief
Clickjacking, also called **UI redressing** (user-interface redressing), is an interface-based attack in which a person is tricked into activating a control on a hidden website while believing they are clicking something else on a decoy page. A common mechanism is to place a target page inside an iframe and layer the decoy content over it. Layout, stacking order, and transparency can make an actionable target control line up with the apparent decoy control. The click is still a real user action within the target site's authenticated session.

## Solution idea
1. Log in to your account on the target website.
2. Go to the exploit server and paste the following HTML template into the Body section: <style> iframe { position:relative; width:$width_value; height: $height_value; opacity: $opacity…
3. Make the following adjustments to the template:
4. Click Store and then View exploit .
5. Hover over Test me and ensure the cursor changes to a hand indicating that the div element is positioned correctly.
6. Once you have the div element lined up correctly, change "Test me" to "Click me" and click Store .
7. Click on Deliver exploit to victim and the lab should be solved.

## Payloads / key values
- `<style> iframe { position:relative; width:$width_value; height: $height_value; opacity: $opacity; z-index: 2; } div { position:absolute; top:$top_value; left:$side_value; z-index: 1; } </style> <div>Test me</div> <iframe src="YOUR-LAB-ID.web-security-academy.net/my-account"></iframe>`
- `YOUR-LAB-ID`
- `src`
- `$height_value`
- `$width_value`
- `$top_value`
- `$side_value`
- `$opacity`
- `top`
- `left`

## Official source
- [PortSwigger Academy: Lab: Basic clickjacking with CSRF token protection](https://portswigger.net/web-security/clickjacking/lab-basic-csrf-protected)
