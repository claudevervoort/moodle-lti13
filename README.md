This project is temporary to build resources and discuss plans on how to bring LTI 1.3 to moodle.

It will hopefully become an actual Moodle Project.

The idea is to bring LTI 1.3 in and grow from there to uplift in general the LTI experience in
moodle.

- [Step 1 is to actually do all LTI 1.3](step1-coreLTI13support.md). With that work, and since
Moodle already supports assignment and grades as well as membership service, this will bring
Moodle to full LTI 1.3 advantage support
- Once this is in place, we could automate the sharing of tool configuration in [step 2](step2-simplerWithRegistrationCallback.md) so that
the user does not have to copy paste keys and ids, just a URL.
- To complete the experience, the deeplinking flow will be extended to be able to pick an
app description. [step3](step3-almostAutomaticWithDeepLinking.md). Pick the app, verify, deploy.
- There is still an inherent issue that external tools deployed at the site are available
to all courses, forcing tools to be deployed at the course level to avoid the noise. 
Tools should be made optional, and require the instructor to pick a
pre-configured tool and explicitly add it. [step4](step4-explicitDeployment.md)