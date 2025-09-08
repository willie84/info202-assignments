# Datasheet: *Mozilla Common Voice Dataset*

Author: *Willie Macharia*

Organization: *UC Berkeley School of Information*


## Motivation

*The questions in this section are primarily intended to encourage dataset creators to clearly articulate their reasons for creating the dataset and to promote transparency about funding interests.*

1. **For what purpose was the dataset created?** Was there a specific task in mind? Was there a specific gap that needed to be filled? Please provide a description.

	* This dataset was created to address a big gap in speech-to-text machine learning applications. Most of the existing speech-to-text datasets focused mainly on English, leaving many languages and communities underrepresented. Among of the underrepresented languages are the Asian and Africa languages. The existing datasets made it difficult to build speech-to-text applications that reflect the diversity of how people actually speak around the world. This dataset was designed to change that, by including a wide range of languages and accents so that speech-to-text technology can  be developed in a more inclusive and accessible to everyone. 


2. **Who created this dataset (e.g. which team, research group) and on behalf of which entity (e.g. company, institution, organization)**?

	* This dataset was created through crowdsourcing model where Mozilla mobilized volunteers across the world to contribute their voices and also validate other volunteers' contributions. Volunteers contributes sentences written in their language and then other volunteers uses Mozilla Common Voice platform to read those sentences aloud. The voices are then validated by volunteers after which Mozilla releases a new version of the datasheet.   

3. **What support was needed to make this dataset?** (e.g. who funded the creation of the dataset? If there is an associated grant, provide the name of the grantor and the grant name and number, or if it was supported by a company or government agency, give those details.)

	* The Common Voice Dataset is funded by Mozilla Foundation. Mozilla Foundations receives donations and philanthropic grants from individual donors and corporate donors. Mozilla Foundation have recognised donations from NVIDIA, Gates Foundation, GIZ and FCDO. 

4. **Any other comments?**

	* This is an active dataset that a new version gets released after every 3 months. It was launched in 2017 and the latest version has audios from 137 different languages across the world. 


## Composition

*Dataset creators should read through the questions in this section prior to any data collection and then provide answers once collection is complete. Most of these questions are intended to provide dataset consumers with the information they need to make informed decisions about using the dataset for specific tasks. The answers to some of these questions reveal information about compliance with the EU’s General Data Protection Regulation (GDPR) or comparable regulations in other jurisdictions.*

1. **What do the instances that comprise the dataset represent (e.g. documents, photos, people, countries)?** Are there multiple types of instances (e.g. movies, users, and ratings; people and interactions between them; nodes and edges)? Please provide a description.

	* The dataset contains audio files in MP3 format with their corresponding text transcriptions. There is an option to add age, sex and accent of the speaker.

2. **How many instances are there in total (of each type, if appropriate)?**

	* The current version of the dataset is Common Voice Corpus 22.0 which has 97,925 audio files with their corresponding transcribed texts. The total combined time of all the audios files is 3,718 hours. 

3. **Does the dataset contain all possible instances or is it a sample (not necessarily random) of instances from a larger set?** If the dataset is a sample, then what is the larger set? Is the sample representative of the larger set (e.g. geographic coverage)? If so, please describe how this representativeness was validated/verified. If it is not representative of the larger set, please describe why not (e.g. to cover a more diverse range of instances, because instances were withheld or unavailable).

	* This dataset is a sample and not a complete set of all spoken languages in the world. It is made up of audios contributed by volunteers who choose to participate through the Common Voice platform. Because contributions depend on who has internet access, interest, and time to record, the dataset does not fully represent all speakers of a language or region. Some languages, like English, have a very large number of audios, while others have only a few. Within each language, certain accents, age groups, and genders are often overrepresented compared to others. Mozilla Foundation and the community work to improve coverage by inviting contributions from underrepresented groups, but the dataset is not statistically representative of the global population. Instead, it reflects the voices of those who actively participated, which means biases in geographic and demographic coverage remain.

4. **What data does each instance consist of?** "Raw" data (e.g. unprocessed text or images) or features? In either case, please provide a description.

	* Each instance contains unprocessed audio file in MP3 format and with its corresponding text.  An instance may have metadata of the speaker that has age, sex and accent.

5. **Is there a label or target associated with each instance?** If so, please provide a description.

	* Each instance has a target label associated with it. The primary label is the text transcription that the speaker read aloud. The dataset is also accompanied by TSV files where each row of the file describes a single audio file. The TSV file row has the following according to the Common Voice Dataset GitHub here: https://github.com/common-voice/cv-dataset/tree/main,
    * client_id – This is hashed ID for the speaker (not personally identifying).

     * path – This is the relative file path to the audio clip. 

    * text – This is the main label which is the expected transcription of the audio. 

    * up_votes / down_votes – These are votes to indicate whether the clip matches the text.

    * age, gender, accent –  These are optional demographic metadata if the speaker chose to provide it.

    * segment – This is also optional which indicates whether the sentence belongs to a specific custom subset. 

6. **Is any information missing from individual instances?** If so, please provide a description, explaining why this information is missing (e.g. because it was unavailable). This does not include intentionally removed information, but might include, e.g. redacted text.

	* The demographic metadata might be missing for some instances as it is optional and depends on the speaker choosing to provide the information or not. The up_votes / down_votes data may also be missing for some audios that have not been reviewed by the community.  

7. **Are relationships between individual instances made explicit (e.g. users' movie ratings, social network links)?** If so, please describe how these relationships are made explicit.

	* No there is no explicit relationships in the dataset as each audio file is treated independently. There is a hashed client_id field associated with each audio, but it is only for tracking audios coming from contributors for data validation. There is no social network links or connections between the users as up_votes and down_votes only indicate if an audio files has been agreed between the users.   

8. **Are there recommended data splits (e.g. training, development/validation, testing)?** If so, please provide a description of these splits, explaining the rationale behind them.

	* Yes, there are recommended data splits in this dataset which are training, dev and test splits. Any demographic data that is present is applied to the entire dataset to create the splits.  According to the Common Voice Dataset GitHub here: https://github.com/common-voice/cv-dataset/tree/main, each version of the dataset has new set of train, dev and test to avoid reproducing and perpetuating demographic skews. The rationale of recreating the splits ensure that machine learning models that are created off this dataset are generalized better to handle unseen speakers and to reduce bias amplification. 

9. **Are there any errors, sources of noise, or redundancies in the dataset?** If so, please provide a description.

	* Yes there are some errors in the dataset. One of the biggest errors is the transcription mismatch but this controlled by having the up_votes and down_votes which helps to mark the audios that doesn't match the text as invalid. Since this is a crowdsourced  project, volunteers record themselves in  uncontrolled environments which may have overlapping voices. Since same text may be spoken by various speakers in different way, machine learning models might find learning accents from different languages very challenging.     *

10. **Is the dataset self-contained, or does it link to or otherwise rely on external resources (e.g. websites, tweets, other datasets)?** If it links to or relies on external resources, a) are there guarantees that they will exist, and remain constant, over time; b) are there official archival versions of the complete dataset (i.e., including the external resources as they existed at the time the dataset was created); c) are there any restrictions (e.g. licenses, fees) associated with any of the external resources that might apply to a future user? Please provide descriptions of all external resources and any restrictions associated with them, as well as links or other access points, as appropriate.

	* This dataset is self-contained and users don't need to click external website to get its access. This dataset is versioned and archived which means users can access same data as per when it was released. The older versions are important for reproducibility. The license for the dataset is CCO (public license) which means users can download, redistribute or modify the dataset with no issues.  

11. **Does the dataset contain data that might be considered confidential (e.g. data that is protected by legal privilege or by doctor-patient confidentiality, data that includes the content of individuals' non-public communications)?** If so, please provide a description.

	* No the dataset does not contain data that is confidential. The text that the contributors read is provided by Mozilla Foundation so it is not personal messages or anything that has personal identifiable information. However, Mozilla Foundation requires the dataset users to declare that they will not go hunting for the people whose voices have been recorded. This is because voice recordings are personal and if one knows how another person talks, they may manage to conceal the other person identity.

12. **Does the dataset contain data that, if viewed directly, might be offensive, insulting, threatening, or might otherwise cause anxiety?** If so, please describe why.

	* No, the dataset does not contain any offensive as the text that contributors read is given to them by Mozilla Foundation. However, through community validation, some audios have marked as invalid that is they do not match the text. There hasn't been any reported cases of whether these unmatching audios are insulting or offensive. 

13. **Does the dataset relate to people?** If not, you may skip the remaining questions in this section.

	* Yes, the dataset relates to the people. it is real people who record themselves speaking loud about the text they have been prompted by the voice platform. 

14. **Does the dataset identify any subpopulations (e.g. by age, gender)?** If so, please describe how these subpopulations are identified and provide a description of their respective distributions within the dataset.

	* Yes, the dataset provides an optional way to provide the metadata of the volunteers. This metadata includes the age, sex and accent/region. Since this demographic data is optional, it is not in all audio files. According to the latest version 22.0, here are the respective distribution of the subpopulations: 
    * Gender
      * 44% Male
      * 18% Female
      * 39% did not provide any information. 
    * Age:
      * 6% < 20 years
      * 25% Between 20 - 29 years 
      * 14% Between 30 - 39 years 
      * 9% Between 40 - 49 years 
      * 5% Between 50 - 59 years 
      * 4% Between 60 - 69 years 
      * 1% Between 70 - 79 years 
      * 36% did not provide any information.

15. **Is it possible to identify individuals (i.e., one or more natural persons), either directly or indirectly (i.e., in combination with other data) from the dataset?** If so, please describe how.

	* Yes but it will be quite hard and indirectly.  With the hashed client_id, you could group audios from each person. You could then listen to audios, and we know that audios are unique to each person that is the way each person speak is unique. If then there is any demographic information available, the identities would be narrowed down. However, according to the dataset, most of the demographic data is often missing.  

16. **Does the dataset contain data that might be considered sensitive in any way (e.g. data that reveals racial or ethnic origins, sexual orientations, religious beliefs, political opinions or union memberships, or locations; financial or health data; biometric or genetic data; forms of government identification, such as social security numbers; criminal history)?** If so, please provide a description.

	* Since this dataset contains human recordings, it will be considered to have some sensitive data as human voice is biometric data. There is also optional demographic data which is age and gender. Combining this two may in a way lead to identification of the contributor.  

17. **Any other comments?**

	* According to Mozilla Foundation, all the users of this dataset have to declare that they will not attempt to identify the contributors. I think this is important as this is dataset that has some sensitive information. 


## Legal & Ethical Considerations

*This section, describes the dataset Legal & Ethical Considerations*

1. **If the dataset relates to people (e.g., their attributes) or was generated by people, were they informed about the data collection?** (e.g., datasets that collect writing, photos, interactions, transactions, etc.)

    * Yes, contributors were informed via the Common Voice platform that to contribute to the datasets, they had to adhere to Mozilla Foundation Common Voice Terms. The terms states that voice recordings and optional demographic information would be collected to create an open dataset for training speech-to-text machine learning applications.

2. **If it relates to other ethically protected subjects, have appropriate obligations been met?** (e.g., medical data might include information collected from animals)

    * Not applicable. This dataset only involves human voice recordings and does not include ethically protected subjects such as animals or medical patients.

3. **If it relates to people, were there any ethical review applications/reviews/approvals?** (e.g. Institutional Review Board applications)

    * In this dataset, there is no formal Institutional Review Board that is publicly documented. According to Mozilla Foundation, the dataset is driven by the public where it is contributed and validated by the public. Mozilla Foundation also follows its internal ethical guidelines and ensures voluntary participation and public use licensing.

4. **If it relates to people, were they told what the dataset would be used for and did they consent?** What community norms exist for data collected from human communications? If consent was obtained, how? Were the people provided with any mechanism to revoke their consent in the future or for certain uses?

    * The voice recordings contributors are informed that their voices would be used to develop speech-to-text machine learning models and applications. Contributors give voluntary consent when they submit recordings on the common voice platform under a CC0 license. Contributors who have an account, have the permission to delete their account and also request Mozilla Foundation to remove their recordings from the dataset. Contributors with no account don't have a way to get their recordings withdrawn from the datasets as contributing with no account means that your voice recordings are associated with a random user id.

5. **If it relates to people, could this dataset expose people to harm or legal action?** (e.g., financial, social or otherwise) What was done to mitigate or reduce the potential for harm?

    * Voice recordings forms part of human biometric data and can be used to identify individuals. Demographic data can also be used to narrow down the identities of the contributors. However, in this dataset, contributors identification has been made difficult by using hashed client IDs which anonymized the contributors.

6. **If it relates to people, does it unfairly advantage or disadvantage a particular social group?** In what ways? How was this mitigated?

    * Since this dataset is created through crowdsourcing, it is inherently that some groups and languages will be overrepresented moreso social groups or areas that have good internet connection. Mozilla Foundation do encourage contributions from the underrepresented groups, but skew remains. Mozilla Foundation also advises the dataset users to account for any bias in their machine learning modelling.

7. **If it relates to people, were they provided with privacy guarantees?** If so, what guarantees and how are these ensured?

    * The privacy guarantee given to voice recordings contributors is that none of their personal identifiable information will be associated with the dataset. A hashed client IDs will be used to identify each contributor but no direct identifies.

8. **Does the dataset comply with the EU General Data Protection Regulation (GDPR)?** Does it comply with any other standards, such as the US Equal Employment Opportunity Act?

    * This dataset does comply with EU GDPR since no personally identifiable information (PII) is being collected and exposed. The US Equal Employment Opportunity Act does not apply to this dataset as no employment-related data is included.

9. **Does the dataset contain information that might be considered sensitive or confidential?** (e.g., personally identifying information)

   * Since human recordings are part of human biometric data, this dataset is considered to have some sensitive data. There is also optional demographic data which is age and gender which is provided by the voice contributor on a voluntary basis.

10. **Any other comments?**

    * The designers of this dataset have done as much as they can to protect the confidentiality of the voice recordings contributors. However, because of the nature of voice recordings being biometric, there is some degree where a person may know who is speaking if they have ever heard them speaking. Therefore, the users of this dataset should use this dataset ethically which is to follow what the Mozilla Foundation have asked the dataset users to do with the dataset.  



## Distribution

*Dataset creators should provide answers to these questions prior to distributing the dataset either internally within the entity on behalf of which the dataset was created or externally to third parties.*

1. **Will the dataset be distributed to third parties outside of the entity (e.g. company, institution, organization) on behalf of which the dataset was created?** If so, please provide a description.

	* Yes. The dataset is open and it is hosted by Mozilla Foundation and a link to download the dataset is provided publicly. Mozilla Foundation researchers, developers, companies, and communities around the world to use the dataset and it is licensed under a CC0 (public domain) license.

2. **How will the dataset will be distributed (e.g. tarball on website, API, GitHub)?** Does the dataset have a digital object identifier (DOI)?

	* The dataset is shared through a link to download a tarball. There exists also a GitHub repository that  describes the dataset here: https://github.com/common-voice/common-voice 

3. **When will the dataset be distributed?**

	* The dataset has already been distributed and its first release was on 24th February 2019. The current version of the dataset is version 22.0 and new versions are released every 3 months.

4. **Will the dataset be distributed under a copyright or other intellectual property (IP) license, and/or under applicable terms of use (ToU)?** If so, please describe this license and/or ToU, and provide a link or other access point to, or otherwise reproduce, any relevant licensing terms or ToU, as well as any fees associated with these restrictions.

	* The dataset is distributed under the Public Licence CC0 meaning the users can use, share and build on top of it without any restrictions. Here is the link to the license definition: https://creativecommons.org/publicdomain/zero/1.0/

5. **Have any third parties imposed IP-based or other restrictions on the data associated with the instances?** If so, please describe these restrictions, and provide a link or other access point to, or otherwise reproduce, any relevant licensing terms, as well as any fees associated with these restrictions.

	* No, there are no third parties imposed IP-based restrictions as everything is under the public license CCO. 

6. **Do any export controls or other regulatory restrictions apply to the dataset or to individual instances?** If so, please describe these restrictions, and provide a link or other access point to, or otherwise reproduce, any supporting documentation.

	* There are no export controls on this dataset. It is available worldwide and anyone can download it and use it. 

7. **Any other comments?**

	* This dataset is open to use and accessible to everyone in the world which aligns well with the goal of the project which is to democratise access to speech-to-text dataset.


## Maintenance

*As with the previous section, dataset creators should provide answers to these questions prior to distributing the dataset. These questions are intended to encourage dataset creators to plan for dataset maintenance and communicate this plan with dataset consumers.*

1. **Who is supporting/hosting/maintaining the dataset?**

	* This dataset is supported and maintained by Mozilla Foundation and the Common Voice community. Mozilla Foundation hosts the dataset on their website and also coordinates the regular dataset updates. The Common Voice community contributes to the voice recordings and validation.

2. **How can the owner/curator/manager of the dataset be contacted (e.g. email address)?**

	* The Mozilla Foundation Common Voice team can be contacted via email address here: commonvoice@mozilla.com. The Common Voice Team can also be contacted through their discord server here: https://discord.com/invite/4TjgEdq25Y.  There is also a discourse channel for topical conversations: https://discourse.mozilla.org/c/voice/239. There is also a Matrix forum for quick chats: https://chat.mozilla.org/#/room/#common-voice:mozilla.org

3. **Is there an erratum?** If so, please provide a link or other access point.

	* There is no formal erratum for this dataset but Mozilla Foundation provides a GitHub repository that shows the changes and fixes that have been made to the dataset. Here is the change logs: https://github.com/common-voice/cv-dataset/blob/main/CHANGELOG.md 

4. **Will the dataset be updated (e.g. to correct labeling errors, add new instances, delete instances)?** If so, please describe how often, by whom, and how updates will be communicated to users (e.g. mailing list, GitHub)?

	* Yes, the dataset is updated regularly and released after every three months. The Common Voice Community also validates various recordings by down voting any recordings that are erroneous. Mozilla Foundation then documents the changes and the updates to the dataset in the GitHub change log here: https://github.com/common-voice/cv-dataset/blob/main/CHANGELOG.md

5. **If the dataset relates to people, are there applicable limits on the retention of the data associated with the instances (e.g. were individuals in question told that their data would be retained for a fixed period of time and then deleted)?** If so, please describe these limits and explain how they will be enforced.

	* Mozilla Foundation has given contributors the ability to decide how long their data can be retained. If a contributor does not want their data to be retained, they can delete their account and request their voice recordings to be removed from dataset. Mozilla Foundation have warned the contributors that some deletion requests may not be honoured if the voice recordings cannot be linked with the user id. https://support.mozilla.org/en-US/kb/common-voice-accounts-managing-account-data

6. **Will older versions of the dataset continue to be supported/hosted/maintained?** If so, please describe how. If not, please describe how its obsolescence will be communicated to users.

	* Yes, the older versions of the dataset will be supported, hosted and maintained by Mozilla Foundation and the Common Voice community. The older versions will still be available through Mozilla Foundation website and any changes documented in the change log file hosted on GitHub. 

7. **If others want to extend/augment/build on/contribute to the dataset, is there a mechanism for them to do so?** If so, please provide a description. Will these contributions be validated/verified? If so, please describe how. If not, why not? Is there a process for communicating/distributing these contributions to other users? If so, please provide a description.

	* Yes, anyone can contribute to the dataset. Anyone can do new voice recordings and at the same time validate existing voice recordings. The existing community members will also have a chance to up vote or down vote any contributions. Updates and new releases will be communicated through the websites and GitHub.

8. **Any other comments?**

	* Through the combined efforts from Mozilla Foundation and the Common Voice Community, this dataset has a good maintenance process.  


* Credits for this GitHub Markdown : https://github.com/JRMeyer/markdown-datasheet-for-datasets/blob/master/DATASHEET.md
## References
  * Ardila, R., Branson, M., Davis, K., Henretty, M., Kohler, M., Meyer, J., Morais, R., Saunders, L., Tyers, F. M. and Weber, G. (2020) "Common Voice: A Massively-Multilingual Speech Corpus". Proceedings of the 12th Conference on Language Resources and Evaluation (LREC 2020). pp. 4211—4215
  * Gebru et al., Proceedings of the 5th Workshop on Fairness, Accountability, and Transparency in Machine Learning, 2018
