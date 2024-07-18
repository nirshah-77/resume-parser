# Resume Parser

Project Overview:
The project aims to develop a resume parsing system that extracts various sections such as skills, certifications, education, and work experience from an inputted resume. Additionally, it extracts the previous and current job titles mentioned in the resume and maps them to the O*NET occupation list, providing the corresponding job code and job title that the user has worked on.

Components:
Resume Parsing Module:

Input: Resume document (PDF, DOCX, DOC, HTML)
Output: Extracted sections such as skills, certifications, education, and work experience

Job Title Mapping Module:

Input: Extracted job titles from the resume
Output: Mapping of job titles to O*NET occupation list, providing job code and job title

Detailed Description:
1. Resume Parsing Module:
Input: The user provides a resume document in PDF, DOCX, DOC or HTML text format.
Processing:
The system utilizes certained pretrianed libraries from Hugging face (https://shorturl.at/nsxBX) to parse the inputted resume and identify specific sections such as skills, certifications, education, and work experience.
Output: Extracted sections are presented to the user, providing a structured overview of the candidate's qualifications and experiences.
2. Job Title Mapping Module:
Input: The system extracts previous and current job titles mentioned in the resume.
Processing:
The extracted job titles are compared against a predefined list of job titles from the O*NET occupation list.
Using techniques such as string matching or semantic similarity using BERT, the system maps each job title to the corresponding O*NET occupation, retrieving the associated job code and job title. To improve the mapping we have used seperate techniques for Job titles with more than one word and one word. For one word we used Levenshtein Distance as Similarity measure and for multiple words we used BERT as a similarity measure.
Output: The system presents the user with a mapping of each job title to the O*NET occupation list, providing the job code and job title that the user has worked on.


## Flow of the Code

1. User adds a resume in any file format (PDF, DOC, DOCX, HTML) that he wants to parse. The algorithm converts any of the file format into txt.
2. A pretrained model (has-abi/distilBERT-finetuned-resumes-sections) from Hugging Face is used classify the information of the parsed resume into 12 different sections.
3. Some operations are performed are to extract the skills of the user dynamically.
4. A python library named find-job-titles (https://pypi.org/project/find-job-titles/) is used to extract the job titles from the resume.
5. In backend, a csv file has been named by using BERT as similarity measure for job titles with more than words and levenshtein distance as similarity measure for one word job titles. This mapping is then mapped with the original O*NET database.
6. The jobs that were extracted from the resume are shown along with he job codes and job titles from the O*NET database. 

## Future Possible Works

Machine Learning Models: Develop machine learning models for job title mapping, allowing for more accurate matching between resume job titles and O*NET occupations.
Web Interface: Create a user-friendly web interface for uploading resumes and viewing extracted information and job title mappings.
Integration with HR Systems: Integrate the resume parsing system with HR management software or applicant tracking systems (ATS) to streamline recruitment processes.
