# PB_Alexor-Workflows

Reusable GitHub Actions workflows til microservices.

## Workflows

| Workflow       | Beskrivelse                      | Outputs                |
|----------------|----------------------------------|------------------------|
| `ci.yml`       | Build og test .NET projekt       | -                      |
| `semantic.yml` | Semantic release, changelog, version.txt | `version`              |
| `cd.yml`       | Build og push Docker image       | `image-tag`            |
| `release.yml`  | Orchestrator: ci → semantic → cd | `version`, `image-tag` |

## Inputs

### ci.yml
| Input               | Required | Default | Beskrivelse       |
|---------------------|----------|---------|-------------------|
| `dotnet-version`    | Nej      | `9.0.x` | .NET SDK version  |
| `working-directory` | Nej      | `.`     | Working directory |

### semantic.yml
| Input            | Required | Default        | Beskrivelse   |
|------------------|----------|----------------|---------------|
| `changelog-file` | Nej      | `CHANGELOG.md` | Changelog fil |
| `version-file`   | Nej      | `version.txt`  | Version fil   |

### cd.yml
| Input             | Required | Default      | Beskrivelse          |
|-------------------|----------|--------------|----------------------|
| `version`         | Ja       | -            | Version tag          |
| `image-name`      | Ja       | -            | Fuldt image navn     |
| `dockerfile-path` | Nej      | `Dockerfile` | Sti til Dockerfile   |
| `build-context`   | Nej      | `.`          | Docker build context |

### release.yml
Kombinerer inputs fra alle tre workflows.
