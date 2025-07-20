# Deployment Setup

## Required Secrets

Go to: Settings → Secrets and variables → Actions

| Secret | Description | Example |
|--------|-------------|---------|
| `DEPLOY_PAT` | GitHub Fine-Grained Personal Access Token | `github_pat_...` |
| `PLUCKY_OUTLET_REPO` | Target repository (owner/repo) | `aleksey-berezin/11ty-scraper-lincoln` |

## GitHub PAT Setup

1. Go to GitHub → Settings → Developer settings → Personal access tokens → Fine-grained tokens
2. Click "Generate new token"
3. **Repository access**: Select "Only select repositories" and choose both staging and target repos
4. **Permissions**: 
   - Repository permissions: `Contents` (Read and write)
   - Actions permissions: `Read and write`
5. Copy token and add as `DEPLOY_PAT` secret

## How It Works

### Automatic Triggers
- **Push to main branch** with changes to property folders:
  - `459 Rock Apartments/**`
  - `Berez/**` 
  - `Lincoln Court Townhomes/**`

### Deployment Process
1. **Detects changed properties** using Git commit history
2. **Clones target repository** (CloudCannon site)
3. **Compares file contents** between staging and production
4. **Copies different files** to `src/_data/scraper/` in target repo
5. **Commits and pushes** changes to production

### File Structure
Files deploy to: `src/_data/scraper/` in target repository
- `459_rock_apartments_listings.json`
- `459_rock_apartments_listings.schema.json`
- `berez_listings.json`
- `berez_listings.schema.json`
- `lincoln_court_townhomes_listings.json`
- `lincoln_court_townhomes_listings.schema.json`

## Manual Trigger
1. Go to Actions tab
2. Select "Deploy Property Listings to CloudCannon"
3. Click "Run workflow"

## Troubleshooting

- **Authentication failed**: Check PAT permissions and repository access
- **Files not deploying**: Verify file contents are different from production
- **Wrong file location**: Files go to `src/_data/scraper/`, not property folders 