# Hidden properties

These columns contain information about our users or process. They live in our database, but should not be returned in API responses or otherwise made publicly accessible.

<table><thead><tr><th width="181">table</th><th width="306.3333333333333">property to hide</th><th>reason/notes</th></tr></thead><tbody><tr><td>data sources</td><td><code>submitter_contact_info</code></td><td>PII</td></tr><tr><td>data sources</td><td><code>submission_notes</code></td><td>intended to be private</td></tr><tr><td>data sources</td><td><code>private_access_instructions</code></td><td>intended to be private</td></tr><tr><td>agencies</td><td><code>submitter_contact</code></td><td>PII</td></tr><tr><td>data requests</td><td><code>submitter_contact_info</code></td><td>PII</td></tr><tr><td>data requests</td><td><code>internal_notes</code></td><td>visible to those with write access</td></tr><tr><td>data requests</td><td><code>connected_volunteers</code></td><td>PII</td></tr><tr><td>volunteers</td><td><code>name</code></td><td>PII</td></tr><tr><td>volunteers</td><td><code>internal_notes</code></td><td>visible to those with write access</td></tr><tr><td>volunteers</td><td><code>discord</code></td><td>PII</td></tr><tr><td>volunteers</td><td><code>github</code></td><td>PII</td></tr><tr><td>volunteers</td><td><code>email</code></td><td>PII</td></tr></tbody></table>