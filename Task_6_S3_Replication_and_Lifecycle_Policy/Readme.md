# Task 6: S3 Replication and Lifecycle Policy

**Objective:**  
Configure replication and lifecycle rules in Amazon S3 to understand cost optimization and backup strategy.

---

### Steps

1. Enable Versioning on Source Bucket
   - Go to **AWS Console → S3 → Source Bucket → Properties → Bucket Versioning → Enable**.
   - Save changes.  

2. Create Destination Bucket
   - Go to **S3 → Create bucket**.
   - Give it a unique name (e.g., `my-replica-bucket-2026`).
   - Enable **versioning**.
   - Configure Block Public Access as required.  

3. Configure Replication
   - Go to Source Bucket → Management → Replication → Add Rule.
   - Scope:All objects or specific prefix/tag.
   - Destination: Select your destination bucket.
   - IAM Role: Create new or select existing with replication permissions.
   - Optional: Replicate delete markers, existing objects.
   - Save the replication rule.

4. Configure Lifecycle Policy
   - Go to Source Bucket → Management → Lifecycle rules → Create rule.
   - Name the rule (e.g., `Task6-Lifecycle`).
   - Scope:All objects or specific prefix/tag.
   - Actions:
     - Transition to S3 Standard-IA after 30 days.  
     - Transition to Glacier after 60 days.  
     - Delete objects after 365 days.  
   - Review and create rule.

5. Verification
   - Upload an object to source bucket → verify replication to destination.
   - Lifecycle rules will execute automatically after the defined period.

---

### Proof Required
1. Screenshot of **versioning enabled** on source bucket.  
2. Screenshot of **replication rule configured.
3. Screenshot of **lifecycle policy configured.
