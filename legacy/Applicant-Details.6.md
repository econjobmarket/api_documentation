## Applicant Details

This particular applicant has made two different applications - one to Position id 1960, the second to position id 1961 (the position id is called posid, naturally enough). Before dealing with these applications, focus on the personal details for a moment.

The personal details are all those contained with the applicant delimiters given by 
```
<xml>
<applicant/>
 
</applicant>
</xml>
```

Many of these fields are empty.  Many are deprecated, but remain for legacy reasons. For example the field `<xml><applicaton_date></xml>`  is no longer used, since application dates are tied to applicants. The fiield `<xml><ejm_applicant_id></xml>` is redundant. Some of the empty fields may be removed in future, but for the moment the view of the data you are seeing is exactly what is in the main database. 

For the moment, the important point to note is that there is no job market paper, or cv attached to an applicant. The reason for this is that this material is more suitably tied to an application. The way the econjobmarket system works is that the candidate owns a collection of files which can be assigned to particular applications. As you are viewing this as a representative of a particular recruiter, you can only access files that are assigned by the candidate to applications that are made to your organization. This is why there are no files at all attached to the applicant object.

At this point we turn to the more complex application objects.