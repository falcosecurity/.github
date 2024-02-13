# Respectful Changes and Code Reviews

This document aims to provide clear guidelines and expectations for code authors contributing to The Falco Project and for reviewers performing code reviews.

Drawing inspiration from the Chromium project, we aim to incorporate their exemplary resources and general guidance into our own practices.

- [Chromium Respectful Changes](https://chromium.googlesource.com/chromium/src/+/main/docs/cl_respect.md)
- [Respectful Code Reviews](https://chromium.googlesource.com/chromium/src/+/main/docs/cr_respect.md)

In The Falco Project, we strive to foster a positive and constructive environment for the review process. Keeping this in mind, we would like to highlight the following points.

## Guidelines for Code Authors

> A special note for first-time contributors:   
>
> We kindly ask you to study the project DNA by examining its history, workflow, and style. It is advisable to start with small patches and code changes to become familiar with the processes and build relationships and trust with the maintainers. If needed, do not hesitate to ask for help and feedback early on. We encourage everyone to work in the open.


- We kindly request that you familiarize yourself with and honor Falco's [governance](https://github.com/falcosecurity/evolution/blob/main/GOVERNANCE.md) and [code of conduct](https://github.com/falcosecurity/evolution/blob/main/CODE_OF_CONDUCT.md).
- Code reviewers, comprising of both [maintainers](https://github.com/falcosecurity/evolution/blob/main/GOVERNANCE.md#maintainers) and [reviewers](https://github.com/falcosecurity/evolution/blob/main/GOVERNANCE.md#reviewers), maintain ownership of the repository in which the Pull Request (PR) has been opened. They can be found in the `OWNERS` files. Each repository features an `OWNERS` file in its root directory and may optionally host additional `OWNERS` files within its subdirectories. Please note that only maintainers possess the permissions to approve PR. Certain repositories, notably [falcosecurity/falco](https://github.com/falcosecurity/falco) and [falcosecurity/libs](https://github.com/falcosecurity/libs), are configured to mandate approval from more than one maintainer.
- Kindly be considerate of reviewers' time and strive to meet all preconditions, including thorough testing and providing sufficient code explanations. Additionally, consider dividing large and high-risk PRs into multiple smaller ones whenever possible.
- Maintainers are committed to performing a first-pass code review within approximately one week. As maintainers and reviewers in The Falco Project are spread across different repositories, we strive to be as responsive as possible for each PR. However, some reviews may take longer, depending on the complexity and scope. As a code author, we encourage you to check the status and feel free to do so on a weekly basis. You can kindly post a comment in the respective PR saying, "I would like to check in on the status. Thank you." This proactive approach helps keep track of progress and facilitates effective communication.
- Additionally, certain reviews may require input from code reviewers with specialized expertise in specific areas. This may result in some delays during the review process. We appreciate your understanding in such cases.
- Once the milestone for the next release has been assigned to your PR, we will make every effort to merge it before the release freeze. However, if it becomes necessary to postpone the patch to the following release, we will notify you and provide a detailed explanation for the decision.
- Code authors are kindly reminded that code reviewers diligently uphold the project's best interests, as outlined in the [maintainers](https://github.com/falcosecurity/evolution/blob/main/GOVERNANCE.md#maintainers) section of the governance. Your cooperation with the reviewers is greatly appreciated, as it contributes to the overall success and advancement of the project.
- Here are a few suggestions to expedite the review process: Please ensure you have thoroughly checked all preconditions to the best of your ability. Additionally, being responsive to your reviewers' comments directly contributes to a continuous review process that benefits all parties involved. Lastly, find the right balance between seeking early input and proceeding without feedback to prevent the submission of large code changes all at once that may not align with the project.
- If you find yourself in a situation where a review is not progressing as expected, or if you feel misunderstood, please reach out to the [core maintainers](https://github.com/falcosecurity/evolution/blob/main/MAINTAINERS.md#core-maintainers) during our weekly [community calls](https://github.com/falcosecurity/community#community-calls). We are here to facilitate discussions and find a solution that aligns with the project's best interests. Your feedback and input are valued and important for the success of the project.


## Guidelines for Code Reviewers

- Kindly maintain a respectful tone while reviewing PRs, always assuming competence and positive intentions. A fresh set of eyes can often spot minor errors that the code author may have overlooked due to their deep involvement in the code changes. The reality is that the majority of PRs benefit from feedback, which is why we have code reviews. Furthermore, please bear in mind that the code base is complex, and newer contributors may lack the context or information that you have acquired over time.
- Given that The Falco Project encompasses various domains of expertise, please be mindful of the diverse backgrounds and areas of expertise of contributors. Recognize that they intend to contribute positively and help ensure project success.
- There is another human being on the other end of the code review process, who also has competing priorities. A continuous review process benefits everyone involved by reducing the need to repeatedly understand the purpose and details of a patch. Moreover, it helps retain contributors who might otherwise be discouraged by an extended review process.
- The code reviewers are responsible for assessing the benefits of the proposed changes for the overall project. Please keep in mind that the code author has invested time and effort into implementing these changes because they see value in Falco. Their motivation may be to overcome limitations and effectively utilize Falco for their specific needs. As reviewers, you can explore various ways to say "yes" and assist in finding a solution that benefits the broader community.
- When requesting code changes, please take the time to explain the reasoning behind the request. Providing a clear explanation helps the code author understand the desired improvements and facilitates effective collaboration.
- Please offer assistance to the code author in testing the code changes, particularly when introducing significant patches. This collaborative effort will help ensure the changes are thoroughly evaluated.
- When expressing your code style preferences, please prioritize specific style modifications that bring clear benefits to the project in terms of performance or maintainability. It is important to avoid excessive emphasis on personal style. This approach promotes inclusivity and respect for different coding styles, as long as they align with the project's best interests.
- Please remember that in the realm of security, striking a balance between speed, caution, and code reorganization is crucial, considering that time is of the essence. This balanced approach allows us to effectively support the necessary capabilities for enhanced threat detection, performance, and scalability benefits within reasonable timelines.

## How the Review Process Works

 The author submits a PR. 
- Automation(@poiana) suggests reviewers for the PR 

  - Determine the set of OWNERS files.
  - choose at least two suggested *reviewers*, trying to find a unique reviewer for every leaf OWNERS file, and request their reviews on the PR. 
- Humans review the PR 
   - Reviewers look for general code quality, correctness, sane software engineering, style, etc.
   - Anyone member of falco can act as a reviewer with the exception of the individual who opened the PR.
   - if the code changes look good to them, a reviewer types ```lgtm``` in a PR comment or review; if they change their mind they ```/lgtm cancel``` 
   - once a reviewer has ```/lgtm```'ed, @poiana applies an ```lgtm``` label to the PR.

- Humans approve the PR 
  - The PR author ```/assign```'s suggested approvers to the PR, and optionally notifies them(eg: pinging @foo for approval)
  - Only people listed in the relevant OWNERS files, either directly or through an alias, can act as APPROVERS, including the individual who opened the PR. 
  - Approvers look for holistic acceptance criteria, including dependencies with other features, forwards/backwards compatibility, API and flag definitions, etc
  - for ``falco`` and ``libs``
  repositeries we require double approval from maintainers and we should explain why and when using this strategy. 
  - If the code changes look good to approver, an approver types ``/approve`` in a PR comment; if they change their mind, they ``/approve`` cancel
  - Alongside the Prow workflow, Falco enforce GitHub reviews too. Simply using ``/approve`` is insufficient; ``approver`` must additionally select the 'Approved' checkbox and click the 'Submit review' button on the GitHub UI
  - A positive GitHub review implies the approved label, so approver doesn't have to write ``/approve`` explicitly; however, ``test-infra`` repositery requires an explicit /approve
  - Once all approver (atleast one) have approved, @poianna applies an ``approved`` label. 

- Automation merges the PR: 
  - if all of the following are TRUE:
    - All required labels are present (eg: lgtm, approved)
    - any blocking labels are missing  (eg: there is no do-not-merge/hold, needs-rebase)
  - And if any of the following are true:
    - there are no presubmit prow jobs configured for this repo 
    - there are presubmit prow jobs configured for this repo, and they all pass after automatically being re-run one last time 
  - then PR will automatically be merged. 

## Thank You Note

Thank you, everyone, for providing value to the Falco community, Falco adopters, and the cybersecurity community as a whole. Your efforts contribute to shifting the information asymmetry to the defenders' advantage.
