# Archi

```mermaid
sequenceDiagram
  autonumber
  Devs->>Github: Commit
  loop PreCommit
      Github->>Github: Terraform Docs Generate Documents
      Github->>Github: Terraform Validate
      Github->>Github: TFLint
      Github->>Github: Pre Hook Generate Documents
  end
  Jenkins-->>Github: Deploy Env
  Jenkins-->>Tools S3: Send Documents
  Jenkins-->>Tools: Call Endpoint to compute
  Tools-->>Tools S3: Retrieve documents
  Tools-->>Tools: Cloudfront Refresh
```
