# LTI 1.3 and above on Moodle

<img src='assets/moodle_13pp.png'>

*This repo is temporary and proposed as a way to build resources and discuss ideas on how to bring
LTI 1.3 to moodle. It will hopefully become an actual Moodle Project.*

With moodle 3.5, the platform has complied to all services making LTI advantage. It is now
lacking support for LTI 1.3 security model to gain full LTI advantage status.

However LTI 1.3 core specifications do not address deployments, and due to the assymetrical
nature of the LTI 1.3 security model, it is now more arduous. So this proposal goes above
just the support of the core specification to propose a deployment model. Hopefully a similar
model will be adopted by other platforms, standardized, and siloed avoided (i.e. use this to
deploy in Moodle, do xx to deploy in zz). See [activation flow](step2-simplerWithActivationFlow.md)
and [deep linking to pick app](step3-almostAutomaticWithDeepLinking.md).



- [Step 1 is to actually do all LTI 1.3](step1-coreLTI13support.md). With that work, and since
Moodle already supports assignment and grades as well as membership service, this will bring
Moodle to **full LTI 1.3 advantage support**
- Once this is in place, we automate the sharing of tool configuration in 
[step 2](step2-simplerWithActivationFlow.md) by introducing an **activation flow**.
- To complete the experience, the deeplinking flow is extended to be able to pick an
app description. [step3](step3-almostAutomaticWithDeepLinking.md). Pick the app, verify, deploy.
- There is still an inherent issue that external tools deployed at the site are available
to all courses, forcing tools to be deployed at the course level to avoid the noise. 
Tools should have the option to be made optional, and require the instructor to pick a
pre-configured tool and explicitly add it. [site tool deployment](optionalCourseDeployment.md)