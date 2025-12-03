# VU-Technology Fork Changes

This fork of [piceaTech/node-gitlab-2-github](https://github.com/piceaTech/node-gitlab-2-github) includes custom enhancements specific to Veterans United Home Loans' migration needs.

## Custom Enhancements

### Enhanced Error Logging for Pull Request Creation (Dec 2024)

**Commit**: `0c4150b`

**Problem**: When migrating GitLab merge requests to GitHub pull requests, the tool would fail with a generic 422 error and assume the branch was already merged. This made debugging difficult when PRs couldn't be created for other reasons.

**Solution**: Enhanced error logging in `src/githubHelper.ts` to capture and display the actual GitHub API error message when a pull request creation fails with a 422 status code.

**Changes**:
- Added detailed error logging for 422 status codes
- Displays GitHub's actual validation error message
- Shows error details from GitHub API response
- Helps diagnose issues like:
  - "No commits between branches"
  - "Branch does not exist"
  - "Pull request already exists"
  - Other GitHub validation errors

**Example Output**:
```
Pull request #19 - GitHub returned 422 error when creating PR from '28-windows-ping-tst' to 'master'
GitHub error message: Validation Failed: {"resource":"PullRequest","code":"custom","message":"No commits between master and 28-windows-ping-tst"}
Cannot create pull request - creating an issue instead to preserve discussion history.
```

**Files Modified**:
- `src/githubHelper.ts` (lines 1032-1053)

---

## Maintenance

This fork is maintained by the Platform Engineering team at Veterans United Home Loans.

**Upstream Sync**: We periodically sync with the upstream repository to incorporate bug fixes and new features from the original project.

**Contributing**: If you have improvements that would benefit the broader community, please consider contributing them back to the [original project](https://github.com/piceaTech/node-gitlab-2-github).

---

## Contact

For issues specific to this fork, please open an issue at:
https://github.com/VU-Technology/node-gitlab-2-github/issues

For general migration tool issues, see the original project:
https://github.com/piceaTech/node-gitlab-2-github/issues
