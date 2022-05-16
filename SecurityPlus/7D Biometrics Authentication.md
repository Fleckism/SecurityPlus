---
tags: [A_D, GRC,section]
---
# EXAM OBJECTIVES COVERED
#addTagsIntoBody 
2.4 Summarize [[authentication]] and authorization design concepts

**Biometric authentication mechanisms allow users to access an account through a physiological feature (fingerprint or iris pattern, for instance) or behavioral pattern.** Being able to summarize the advantages and drawbacks of biometric mechanisms will allow you to support the deployment and use of these technologies.
# BIOMETRIC AUTHENTICATION 

The first step in setting up biometric authentication is enrollment. The chosen biometric information is scanned by a biometric reader and converted to binary information. There are generally two steps in the scanning process:

1.  A sensor module acquires the biometric sample from the target.
2.  A feature extraction module records the features in the sample that uniquely identify the target.

The biometric template is kept in the authentication server's database. When the user wants to access a resource, he or she is re-scanned, and the scan is compared to the template. If they match to within a defined degree of tolerance, access is granted.

Several pattern types can be used to identify people biometrically. These can be categorized as physical (fingerprint, eye, and facial recognition) or behavioral (voice, signature, and typing pattern matching). Key metrics and considerations used to evaluate the efficacy rate of biometric pattern acquisition and matching and suitability as an authentication mechanism include the following:

-   False Rejection Rate ([[FRR]])—where a legitimate user is not recognized. This is also referred to as a Type I error or false non-match rate ([[FNMR]]). FRR is measured as a percentage.
-   False Acceptance Rate ([[FAR]])—where an interloper is accepted (Type II error or false match rate [[FMR]]). FAR is measured as a percentage.  
      
    False rejection cause inconvenience to users, but false acceptance can lead to security breaches, and so is usually considered the most important metric.
-   Crossover Error Rate ([[CER]])—the point at which FRR and FAR meet. The lower the CER, the more efficient and reliable the technology.  
      
    Errors are reduced over time by tuning the system. This is typically accomplished by adjusting the sensitivity of the system until CER is reached.
-   **Throughput** (**speed**)—the time required to create a template for each user and the time required to authenticate. This is a major consideration for high traffic access points, such as airports or railway stations.
-   Failure to Enroll Rate ([[FER]])—incidents in which a template cannot be created and matched for a user during enrollment.
-   **Cost/implementation**—some scanner types are more expensive, whereas others are not easy to incorporate on mobile devices.
-   Users can find it intrusive and threatening to privacy.
-   The technology can be discriminatory or inaccessible to those with disabilities.
# FINGERPRINT RECOGNITION

Physiologic biometric features represent a something you are factor. They include fingerprint patterns, iris or retina recognition, or facial recognition. 

Fingerprint recognition is the most widely implemented biometric authentication method. The technology required for scanning and recording fingerprints is relatively inexpensive and the process quite straightforward. A fingerprint sensor is usually implemented as a small capacitive cell that can detect the unique pattern of ridges making up the pattern. The technology is also non-intrusive and relatively simple to use, although moisture or dirt can prevent readings.

![Box reads "Great! Now repeat. Move your finger slightly to add all the different parts of your fingerprint" above a circle with a fingerprint graphic.](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/6815-1599771799736.png)

Configuring fingerprint recognition on an Android smartphone. (Android is a trademark of Google LLC.)

The main problem with fingerprint scanners is that it is possible to obtain a copy of a user's fingerprint and create a mold of it that will fool the scanner ([tomsguide.com/us/iphone-touch-id-hack,news-20066.html](https://www.tomsguide.com/us/iphone-touch-id-hack,news-20066.html)). These concerns are addressed by vein matching scanners, or vascular biometrics. This requires a more complex scanner—an infrared light source and camera—to create a template from the unique pattern of blood vessels in a person's finger or palm.
# FACIAL RECOGNITION

Facial recognition records multiple indicators about the size and shape of the face, like the distance between each eye, or the width and length of the nose. The initial pattern must be recorded under optimum lighting conditions; depending on the technology, this can be a lengthy process. Again, this technology is very much associated with law enforcement, and is the most likely to make users uncomfortable about the personal privacy issues. Facial recognition suffers from relatively high false acceptance and rejection rates and can be vulnerable to spoofing. Much of the technology development is in surveillance, rather than for authentication, although it is becoming a popular method for use with smartphones.

The limitations of facial recognition can be overcome by scanning more detailed features of the eye:

-   **[[Retinal scan]]**—an infrared light is shone into the eye to identify the pattern of blood vessels. The arrangement of these blood vessels is highly complex and typically does not change from birth to death, except in the event of certain diseases or injuries. **Retinal scanning is therefore one of the most accurate forms of biometrics.** Retinal patterns are very secure, but the equipment required is expensive and the process is relatively intrusive and complex. False negatives can be produced by disease, such as cataracts.

![](https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8983-1599771799888.png)

A retinal scan uses an **infrared** light to identify the pattern of blood vessels in the eye. (Photo by Ghost Presenter on Unsplash.)

-   **Iris scan**—matches patterns on the surface of the eye using **near-infrared** imaging and so is less intrusive than retinal scanning (the subject can continue to wear glasses, for instance) and a lot quicker. Iris scanners offer a similar level of accuracy as retinal scanners but are much less likely to be affected by diseases. Iris scanning is the technology most likely to be rolled out for high-volume applications, such as airport security. There is a chance that an iris scanner could be fooled by a high-resolution photo of someone's eye.
# BEHAVIORAL TECHNOLOGIES

"Something you do" refers to behavioral biometric pattern recognition. Rather than scan some attribute of your body, a template is created by analyzing a behavior, such as typing, writing a signature, or walking/moving. The variations in motion, pressure, or gait are supposed to uniquely verify each individual. In practice, however, these methods are subject to **higher error rates,** and are much more troublesome for a subject to perform.

-   **Voice recognition**—relatively cheap, as the hardware and software required are built into many standard PCs and mobiles. However, obtaining an accurate template can be difficult and time-consuming. Background noise and other environmental factors can also interfere with logon. Voice is also subject to impersonation.
-   **Gait analysis**—produces a template from human movement (locomotion). The technologies can either be camera-based or use smartphone features, such as an accelerometer and gyroscope.
-   **Signature recognition**—==signatures are relatively easy to duplicate==, but it is more difficult to fake the actual signing process. Signature matching records the user applying their signature (stroke, speed, and pressure of the stylus).
-   Typing—matches the speed and pattern of a user’s input of a passphrase.

Some biometric and behavioral technologies might be used for purposes other than logon authentication:

-   _Biometric identification_ refers to matching people to a database, as opposed to authenticating them per se. For example, if an individual crossing the floor of the data center does not produce a match for gait analysis, the system may raise a security alert ([https://www.g4s.com/news-and-insights/insights/2017/12/06/keeping-data-centres-secure](https://www.g4s.com/news-and-insights/insights/2017/12/06/keeping-data-centres-secure)).
-   _Continuous authentication_ verifies that the user who logged on is still operating the device. For example, if a user successfully authenticates to a smartphone using a fingerprint, the device continues to monitor key motion and pressure statistics as the device is held and manipulated. If this deviates from the baseline, detection system would lock the phone. This sort of technology is not available on the market (at the time of writing), but it is the subject of numerous research projects.
