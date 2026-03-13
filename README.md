# org-devops-workflows



brew install gh

gh --version

2️⃣ Login to GitHub

gh auth login
GitHub.com
HTTPS
Login with browser


3️⃣ Set Your Organization Name

ORG_NAME=narendarkumar4944-blip

4️⃣ Create the Workflow File Locally

nano jira-check.yml

5️⃣ Encode the File (Important)

base64 jira-check.yml > jira-check.b64

6️⃣ Run the Script

ORG_NAME=narendarkumar4944-blip

for repo in $(gh repo list $ORG_NAME --limit 200 --json name -q '.[].name')
do
  gh api repos/$ORG_NAME/$repo/contents/.github/workflows/jira-check.yml \
  --method PUT \
  --field message="Add Jira validation workflow" \
  --field content="$(base64 -i jira-check.yml)"
