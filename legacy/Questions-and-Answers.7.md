##Questions and Answers

The next step is to decipher the information in the application questions and answers. In this section, I'll go through how to retrieve the information from the applicant object that was described earlier. Retrieving custom questions and answers directly is discussed in the next section. 

The applicant object lists responses first. To avoid a network request, the text associated with the questions are listed after the responses in exactly the same order. I'll explain those briefly later.

Here is the first of the responses associated with our example application, copied from the applicant object described above:
The first question asks for the applicants CV.  I figured that out by noticing that the first question listed in the applicant object that I retrieved before is about the cv.  The answer is given by the first response as follows:
```
 <responses>
      <index>6</index>
      <template_id>5</template_id>
      <question_id>21680</question_id>
      <piece_id>56441</piece_id>
      <varstring>299449</varstring>
      <vartext />
    </responses>
```

The index gives the order in which the questions and their answer appear on the ejm application form. Higher indexes appear lower in the form. Since the lowest index in the list of responses is 6, this is the first question and answer on the form. The template_id allows you to recover the html code that was used to render the question and answer on the ejm website. Since you probably have your own way of displaying answers, you probably won't be interested in this. The question_id can be used to look up the text associated with the question to which the response you are looking at is an answer. The piece_id is just a number used to match a question and answer in the ejm database, and it is of no interest here, though we'll use it later when we retrieve the questions and answers directly. The response to the question is given either in the field varstring or vartext, depending on the question type (essay type answers are given in vartext, most short answers are given in varstring). The question type can be discerned from the template id.<p>

The list of easy templates at ejm is
```
| Section Header  |           1 |
| Plain Text      |           2 |
| Blank Line      |           3 |
| Simple Text Box |           4 |
| File Upload     |           5 |
| Drop-Down Menu  |           6 |
| Radio Buttons   |           7 |
| Check Boxes     |           8 |
```
The template id 5 means that the first question asked for a file, which will come as a blobid. The blobid of the file that the applicant assigned to this question is given in the varstring field as 299449.  We'll get back to how to fetch the file in a moment.

You can look up the full text associated with this question by using the getTable method, which I'll explain below. Alternatively, you can look at the applicant object for the list of questions, and match the question with the answer given above.

Here is the code for the questions in the candidate object.
```
  <questions>C.V.:  </questions>
    <questions>Job-Market Paper::  </questions>
    <questions>Additional paper (optional)::  </questions>
    <questions>Where did you learn about this position?:  &quot;- nothing selected -&quot;,&quot;Job Openings for Economists&quot;,&quot;Our Economics Website&quot;,&quot;National Economic Association website&quot;,&quot;Inomics&quot;,&quot;Other&quot;:  </questions>
    <questions>Title of your job-market paper:&lt;br /&gt;
(Abbreviate if necessary):  </questions>
```

The questions listed in the code segment correspond with the answers given in the responses segment given above. The first response gives a blobid in the vartex block that matches the first question "C.V".

If all you want to do is render this question and its answer on an html page, then all that really needs to be done is to render a clickable url that will open the file with whatever method you are using.  If you are trying to match this question and answer to a question and answer in your own database, then you need to devise your own algorithm and logic for doing that.

There is another section of the applicant object that works in a simpler way. I'll briefly mention it before going on to handling of blobs. Here are the references associated with the example applicant:
```
  <references>
      <fname>Yoram</fname>
      <lname>Halevy</lname>
      <department>Economics</department>
      <institution>University of British Columbia</institution>
      <letter>299454</letter>
    </references>
    <references>
      <fname>Hao</fname>
      <lname>Li</lname>
      <department />
      <institution>University of British Columbia</institution>
      <letter>299491</letter>
    </references>
    <references>
      <fname>Michael</fname>
      <lname>Peters</lname>
      <department>Department of Economics</department>
      <institution>University of British Columbia</institution>
      <letter>299457</letter>
    </references>
```

There are three of them. The fields are easy to interpret, and the blobid associated with the letters the referees sent are in the letter field. These are always blobids, so all that is left is to open the corresponding blobs.