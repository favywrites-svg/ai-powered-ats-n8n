# AI-Powered Applicant Tracking System (ATS)

An AI-powered Applicant Tracking System built with n8n, Google Workspace, and Gemini to automate CV screening and candidate management.

## Overview

This project automates the initial stage of a recruitment process, from collecting candidate applications to screening CVs, making recommendations, sending candidate emails, and tracking application status.

The system is designed to reduce repetitive manual work involved in reviewing applications while keeping recruiters in control of candidates that require further review.

## Problem

Recruitment teams can receive a large number of applications for a single position. Manually downloading CVs, extracting candidate information, comparing qualifications against job requirements, and communicating with candidates can become repetitive and time-consuming.

This workflow automates the initial screening process while allowing recruiters to manually review candidates where the AI assessment is uncertain.

## Solution

The system uses n8n to connect the application form, Google Workspace, AI screening, and email communication into one automated workflow.

When a candidate submits an application:

1. The application is captured in Google Sheets.
2. The candidate's CV is retrieved from Google Drive.
3. The CV text is extracted automatically.
4. Candidate information is combined with the relevant job description.
5. Gemini evaluates the CV against the job requirements.
6. The AI generates a match score, strengths, missing requirements, summary, and recommendation.
7. The candidate is routed into one of three outcomes:
   - **Interview** – candidate receives an interview invitation.
   - **Review** – application is stored for manual HR review.
   - **Reject** – candidate receives an application update.
8. Screening results and application status are stored in the ATS database.

## Workflow

```text
Google Form
     ↓
Google Sheets
     ↓
Retrieve CV from Google Drive
     ↓
Extract CV Text
     ↓
Candidate Details + Job Description
     ↓
AI Screening
     ↓
Match Score + Recommendation
     ↓
   Switch
   ↙  ↓  ↘
Interview Review Reject
   ↓      ↓      ↓
Email   HR Queue  Email
