---
title: 'A billion medical images are exposed online, as doctors ignore warnings'
date: 2020-01-11T14:47:00+01:00
draft: false
---

This story was reported in partnership with health news site

[The Mighty.](https://themighty.com/2020/01/unsecured-medical-image-data-threat-to-patients)

Every day, millions of new medical images containing the personal health information of patients are spilling out onto the internet.

Hundreds of hospitals, medical offices and imaging centers are running insecure storage systems, allowing anyone with an internet connection and free-to-download software to access over 1 billion medical images of patients across the world.

About half of all the exposed images, which include X-rays, ultrasounds and CT scans, belong to patients in the United States.

Yet despite warnings from security researchers who have spent weeks alerting hospitals and doctors’ offices to the problem, many have ignored their warnings and continue to expose their patients’ private health information.

“It seems to get worse every day,” said Dirk Schrader, who led the research at Germany-based security firm Greenbone Networks, which has been monitoring the number of exposed servers for the past year.

The problem is well-documented. Greenbone found 24 million patient exams storing more than 720 million medical images in September, which first [unearthed the scale](https://www.greenbone.net/en/unprotected-patient-data-on-the-internet-a-massive-global-data-leak/) of the problem [as reported by ProPublica](https://www.propublica.org/article/millions-of-americans-medical-images-and-data-are-available-on-the-internet). Two months later, the number of exposed servers had increased by [more than half](https://www.greenbone.net/en/the-good_bad_ugly-amount_is_rising/), to 35 million patient exams, exposing 1.19 billion scans and representing a considerable violation of patient privacy.

But the problem shows little sign of abating. “The amount of data exposed is still rising, even considering the amount of data taken offline due to our disclosures,” said Schrader.

If doctors fail to take action, he said the number of exposed medical images will hit a new high “in no time.”

![](https://techcrunch.com/wp-content/uploads/2020/01/patient-scan.png)

Over a billion medical images remain exposed. Experts say the number is getting worse, not better. (Image: supplied)

Researchers say the problem is caused by a common weakness found on the servers used by hospitals, doctors’ offices and radiology centers to store patient medical images.

A decades-old file format and industry standard known as DICOM was designed to make it easier for medical practitioners to store medical images in a single file and share them with other medical practices. DICOM images can be viewed using any of the free-to-use apps, as would any radiologist. DICOM images are typically stored in a picture archiving and communications system, known as a PACS server, allowing for easy storage and sharing. But many doctors’ offices disregard security best practices and connect their PACS server directly to the internet without a password.

These unprotected servers not only expose medical imaging but also patient personal health information. Many patient scans include cover sheets baked into the DICOM file, including the patient’s name, date of birth and sensitive information about their diagnoses. In some cases, hospitals use a patient’s Social Security number to identify patients in these systems.

Lucas Lundgren, a Sweden-based security researcher, spent part of last year looking at the extent of exposed medical image data. In November, he demonstrated to TechCrunch how easy it was for anyone to view medical data from exposed servers. In just a few minutes, he found one of the largest hospitals in Los Angeles exposing tens of thousands of patients’ scans dating back several years. The server was later secured.

Some of the largest hospitals and imaging centers in the United States are the biggest culprits of exposing medical data. Schrader said the exposed data puts patients at risk of becoming “perfect victims for medical insurance fraud.”

Yet, patients are unaware that their data could be exposed on the internet for anyone to find.

The Mighty, which [examined the effect on patients](https://themighty.com/2020/01/unsecured-medical-image-data-threat-to-patients), found exposed medical information puts patients at a greater risk of insurance fraud and identity theft. Exposed data can also erode the relationship between patients and their doctors, leading to patients becoming less willing to share potentially pertinent information.

As part of our investigation, we found a number of U.S. imaging centers storing decades of patient scans.

One patient, whose information was exposed following a visit to an emergency room in Florida last year, described her exposed medical data as “scary” and “uncomfortable.” Another with a chronic illness had regular scans at a hospital in California over a period of 30 years. And one unprotected server at one of the largest military hospitals in the United States exposed the names of military personnel and medical images.

But even in cases of patients with only one or a handful of medical images, the exposed data can be used to infer a picture of a person’s health, including illnesses and injuries.

![](https://techcrunch.com/wp-content/uploads/2020/01/exposed-health-data.png)

Many patient scans include cover sheets containing personal health information baked into the file. (Image: supplied)

In an effort to get the servers secured, Greenbone contacted more than a hundred organizations last month about their exposed servers. Many of the smaller organizations subsequently secured their systems, resulting in a small drop in the overall number of exposed images. But when the security company contacted the 10 largest organizations, which accounted for about one-in-five of all exposed medical images, Schrader said there was “no response at all.”

Greenbone privately shared names of the organizations to allow TechCrunch to follow up with each medical office, including a health provider with three hospitals in New York, a radiology company in Florida with a dozen locations and a major California-based hospital. (We’re not naming the affected organizations to limit the risk of exposing patient data.)

Only one organization secured its servers. Northeast Radiology, a partner of Alliance Radiology, had the largest cache of exposed medical data in the U.S., according to Greenbone’s data, with more than 61 million images on about 1.2 million patients across its five offices. The server was secured only after TechCrunch followed up a month after Greenbone first warned the organization of the exposure.

Alliance spokesperson Tracy Weise declined to comment.

Schrader said if the remaining affected organizations took their exposed systems off the internet, almost 600 million images would “disappear” from the internet.

Experts who have warned about exposed servers for years say medical practices have few excuses. Yisroel Mirsky, a security researcher who has studied security vulnerabilities in medical equipment, said [last year](https://www.dicomstandard.org/using/security/) that security features set out by [the standards body](https://www.dicomstandard.org/using/security/) that created and maintains the DICOM standard have “largely been ignored” by the device manufacturers.

Schrader did not lay blame on the device manufacturers. Instead, he said it was “pure negligence” that doctor’s offices failed to properly configure and secure their servers.

Lucia Savage, a former senior privacy official at the U.S. Department of Health and Human Services, said more has to be done to improve security across the healthcare industry — especially at the level of smaller organizations that lack resources.

“If the data is personal health information, it is required to be secured from unauthorized access, which includes finding it on the internet,” said Savage. “There is an equal obligation to lock the file room that contains your paper medical records as there is to secure digital health information,” she said.

Medical records and personal health data are highly protected under U.S. law. The Health Insurance Portability and Accountability Act (HIPAA) created the “security rule,” which included technical and physical safeguards designed to protect electronic personal health information by ensuring the data is kept private and secure. The law also holds healthcare providers accountable for any security lapses. Running afoul of the law can lead to severe penalties.

> “As Health and Human Services aggressively pushes to permit a wider range of parties to have access to the sensitive health information of American patients without traditional privacy protections attaching to that information, HHS’s inattention to this particular incident becomes even more troubling.”  
> Sen. Mark Warner (D-VA)

The government last year [fined one Tennessee-based medical imaging company $3 million](https://www.hhs.gov/about/news/2019/05/06/tennessee-diagnostic-medical-imaging-services-company-pays-3000000-settle-breach.html) for inadvertently exposing a server containing over 300,000 protected patient data.

Deven McGraw, who was the top privacy official in the Health and Human Services’ enforcement arm — the Office of Civil Rights, said if security assistance was more available to smaller providers, the government could focus its enforcement efforts on providers that willfully ignore their security obligations.

“Government enforcement is important, as is guidance and support for lower resourced providers and easy-to-deploy solutions that are built into the technology,” said McGraw. “It may be too big of a problem for any single law enforcement agency to truly put a dent in.”

Since the scale of exposed medical servers was first revealed in September, Sen. Mark Warner (D-VA) called for answers from Health and Human Services. Warner acknowledged that the number of U.S.-based exposed servers had decreased — 16 servers storing 31 million images — but told TechCrunch that “more needs to be done.”

“To my knowledge, Health and Human Services has done nothing about it,” Warner told TechCrunch. “As Health and Human Services aggressively pushes to permit a wider range of parties to have access to the sensitive health information of American patients without traditional privacy protections attached to that information, HHS’s inattention to this particular incident becomes even more troubling,” he added.

Health and Human Services’ Office for Civil Rights said it does not comment on individual cases but defended its enforcement actions.

“OCR has taken enforcement action in the past to address violations concerning unprotected storage servers, and continues robust enforcement of the HIPAA rules,” said the spokesperson.

“We will continue doing our best to improve the global situation of unprotected systems,” said Schrader. But he said there was not much more he can do beyond warn organizations of their exposed servers.

“Then it’s a question for the regulators,” he said.

  
  
from Hacker News https://ift.tt/36IJYSq