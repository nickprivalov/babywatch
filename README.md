# BabyWatch

This is a super simple app with one purpose: get people to stop bugging my wife asking if
the baby is here yet.

The page should reliably tell a visiting user whether nothing has happened yet,
labor has begun, or the baby has arrived.

---

## Architecture

The app is meant to be a super simple web page.

When stored on S3, the root `index.html` will have a unique metadata tag to "record" the active state: `x-amz-meta-baby-status: <state>`
(with `<state>` being `nothing-yet`, `on-the-way`, or `with-the-parents`).

On my own phone, using the **Tasker** app for Android, shortcuts setup on the home screen will
fire off API calls that modify the metadata for `index.html` (done by running a typical S3 `copyObject` function call
with a different metadata tag value).

The metadata tag of `index.html` gets fetched when the page loads and determines what content to display on the page
(i.e. whether the baby is here or not).

Is this meant to flex any major skills? Not really. Just meant to be a really quick thing whipped up so my wife and I can tell people
"if you want to know, just go to babyvic.nickpriv.net"
