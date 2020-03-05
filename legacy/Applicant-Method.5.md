## Applicant Method

Now take an applicant id from the previous page - in this example I'll use `aid=18213`.  I can discover everything I need to know about him or her by using the applicant method.

Using SOAP, I would retrieve the data using the following
```
 $client->call("getApplicant", array("username" => "my_password",
                                         "password" => "my_username",
                                         "database" => "my_database",
                                         "id" => 18213,                                                                                                                                                   
                                         "method" => XML,
                                                                              ));
```

Using ReST I would use the url
```
https://backend.econjobmarket.org/rest/my_database/XML/Applicant/18213
```

Here is the applicant object in XML Format as it is returned by these two requests:
```
<xml>
<applicant>
  <error>0</error>
  <id>18213</id>
  <aid>18213</aid>
  <enrolldate>2013-01-19 17:33:04</enrolldate>
  <changedate />
  <email>montoyaubc@gmail.com</email>
  <pin>MP995705</pin>
  <spin />
  <snonce />
  <fname>M</fname>
  <mname />
  <lname>Peters3</lname>
  <addr1>ubc</addr1>
  <addr2 />
  <city>vancouver</city>
  <state>bc</state>
  <zip>v6k1x1</zip>
  <country>canada</country>
  <phone>6543210</phone>
  <fax />
  <url>http://</url>
  <category_id>17</category_id>
  <categories>22</categories>
  <degreetype>masters</degreetype>
  <degreeinst>ubc</degreeinst>
  <degreebegyear>2007</degreebegyear>
  <degreeendyear>2009</degreeendyear>
  <curpos>na</curpos>
  <curinst>ubc</curinst>
  <ethnic />
  <ethnicity />
  <race />
  <gender>withheld</gender>
  <is_contactok>0</is_contactok>
  <cv_url />
  <ackdate>2013-01-19</ackdate>
  <nationality />
  <status>0</status>
  <conferences />
  <statusinactivedate />
  <last_revised_time />
  <application_date>Dec-31-1969</application_date>
  <ejm_applicant_id>18213</ejm_applicant_id>
  <application>
    <appid>224052</appid>
    <posid>1960</posid>
    <appdate>1358638887</appdate>
    <adtitle>Test Ad for Njoyn will not display at EJM</adtitle>
    <responses>
      <index>6</index>
      <template_id>5</template_id>
      <question_id>21680</question_id>
      <piece_id>56441</piece_id>
      <varstring>299449</varstring>
      <vartext />
    </responses>
    <responses>
      <index>7</index>
      <template_id>5</template_id>
      <question_id>21681</question_id>
      <piece_id>56445</piece_id>
      <varstring>299450</varstring>
      <vartext />
    </responses>
    <responses>
      <index>8</index>
      <template_id>5</template_id>
      <question_id>21682</question_id>
      <piece_id>56449</piece_id>
      <varstring>299451</varstring>
      <vartext />
    </responses>
    <responses>
      <index>13</index>
      <template_id>6</template_id>
      <question_id>21687</question_id>
      <piece_id>56466</piece_id>
      <varstring>4</varstring>
      <vartext />
    </responses>
    <responses>
      <index>16</index>
      <template_id>4</template_id>
      <question_id>21690</question_id>
      <piece_id>56475</piece_id>
      <varstring>my jmp</varstring>
      <vartext />
    </responses>
    <questions>C.V.:  </questions>
    <questions>Job-Market Paper::  </questions>
    <questions>Additional paper (optional)::  </questions>
    <questions>Where did you learn about this position?:  &quot;- nothing selected -&quot;,&quot;Job Openings for Economists&quot;,&quot;Our Economics Website&quot;,&quot;National Economic Association website&quot;,&quot;Inomics&quot;,&quot;Other&quot;:  </questions>
    <questions>Title of your job-market paper:&lt;br /&gt;
(Abbreviate if necessary):  </questions>
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
  </application>
  <application>
    <appid>224053</appid>
    <posid>1961</posid>
    <appdate>1358638923</appdate>
    <adtitle>Second Test Ad - will not display</adtitle>
    <responses>
      <index>2</index>
      <template_id>7</template_id>
      <question_id>21693</question_id>
      <piece_id>56483</piece_id>
      <varstring>1</varstring>
      <vartext />
    </responses>
    <responses>
      <index>3</index>
      <template_id>8</template_id>
      <question_id>21692</question_id>
      <piece_id>56481</piece_id>
      <varstring>3</varstring>
      <vartext />
    </responses>
    <responses>
      <index>4</index>
      <template_id>7</template_id>
      <question_id>21694</question_id>
      <piece_id>56485</piece_id>
      <varstring>1</varstring>
      <vartext />
    </responses>
    <responses>
      <index>6</index>
      <template_id>5</template_id>
      <question_id>21696</question_id>
      <piece_id>56488</piece_id>
      <varstring>299449</varstring>
      <vartext />
    </responses>
    <responses>
      <index>7</index>
      <template_id>5</template_id>
      <question_id>21697</question_id>
      <piece_id>56492</piece_id>
      <varstring>299450</varstring>
      <vartext />
    </responses>
    <responses>
      <index>8</index>
      <template_id>5</template_id>
      <question_id>21698</question_id>
      <piece_id>56496</piece_id>
      <varstring>299451</varstring>
      <vartext />
    </responses>
    <questions>Are you a Canadian Citizen or a Permanent Resident of Canada?:  &quot;Yes&quot;,&quot;No|:  </questions>
    <questions>Which fields best describe your area of Expertise:  &quot;Macroeconomics&quot;, &quot;Microeconomics&quot;, &quot;Banking&quot;, &quot;Other&quot;:  </questions>
    <questions>What is your Gender? (you can refuse to answer):  &quot;Male&quot;,&quot;Female&quot;,&quot;No Response&quot;:  </questions>
    <questions>Please provide a url for the most up to data copy of your cv. This link should include http:// and should point to a pdf file, not to a website.:  </questions>
    <questions>Provide a cv from the files you have saved at econjobmarket.:  </questions>
    <questions>Your job market paper - select from your saved files here.:  </questions>
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
  </application>
</applicant>
</xml>
```
