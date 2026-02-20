import { z } from 'zod';
import { createEndpoint, JobApplications } from 'zite-integrations-backend-sdk';

export default createEndpoint({
  description: 'Submit a job application with personal info, work experience, education, and file uploads',
  authenticated: true,
  inputSchema: z.object({
    fullName: z.string(),
    email: z.string().email(),
    phoneNumber: z.string(),
    location: z.string(),
    positionAppliedFor: z.string(),
    availableStartDate: z.string(),
    currentEmployer: z.string().optional(),
    jobTitle: z.string().optional(),
    employmentDates: z.string().optional(),
    jobResponsibilities: z.string().optional(),
    educationLevel: z.string().optional(),
    institution: z.string().optional(),
    degree: z.string().optional(),
    resumeUrl: z.string().optional(),
    coverLetterUrl: z.string().optional(),
  }),
  outputSchema: z.object({
    success: z.boolean(),
    applicationId: z.string(),
  }),
  execute: async ({ input }) => {
    const application = await JobApplications.create({
      record: {
        fullName: input.fullName,
        email: input.email,
        phoneNumber: input.phoneNumber,
        location: input.location,
        positionAppliedFor: input.positionAppliedFor,
        availableStartDate: input.availableStartDate,
        currentEmployer: input.currentEmployer,
        jobTitle: input.jobTitle,
        employmentDates: input.employmentDates,
        jobResponsibilities: input.jobResponsibilities,
        educationLevel: input.educationLevel,
        institution: input.institution,
        degree: input.degree,
        resume: input.resumeUrl ? [{ url: input.resumeUrl }] : undefined,
        coverLetter: input.coverLetterUrl ? [{ url: input.coverLetterUrl }] : undefined,
        submittedAt: new Date().toISOString(),
      },
    });

    return {
      success: true,
      applicationId: application.id,
    };
  },
});
