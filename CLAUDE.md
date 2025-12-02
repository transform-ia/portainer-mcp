# Claude Code Working Notes

## Repository Purpose

MCP (Model Context Protocol) server providing Portainer API integration. Manages Docker containers, stacks, and environments via Portainer.

## Plugin Usage

### When to use plugins

- `/go:cmd-build` - Build Go binary
- `/go:cmd-test` - Run Go tests
- `/go:cmd-lint` - Lint Go code with golangci-lint
- `/go:cmd-tidy` - Update Go dependencies
- `/docker:cmd-lint` - Lint Dockerfile
- `/mcp:cmd-test` - Test MCP server connectivity
- `/orchestrator:detect` - Auto-detect appropriate plugin

### Available plugins

- go, docker, mcp, github, markdown, orchestrator

## Development Workflow

**Build Process:**

1. Modify Go code in `cmd/` or `pkg/`
2. Run `/go:cmd-lint` and `/go:cmd-test`
3. Build binary: `/go:cmd-build .`
4. Build Docker image: `docker build -t portainer-mcp:test .`
5. Test MCP server: `/mcp:cmd-test portainer-mcp`
6. Commit changes

## MCP Server Capabilities

**Tools provided:**

- List and manage containers
- Deploy and manage stacks
- Query container logs and stats
- Manage Docker volumes and networks
- Environment and endpoint management

**Integration:**

- Connects to Portainer REST API
- Requires Portainer API token via environment variable
- Supports multiple Portainer environments

## Project Structure

- `cmd/portainer-mcp/` - Main entry point
- `pkg/mcp/` - MCP protocol implementation
- `pkg/portainer/` - Portainer API client library
- `Dockerfile` - Multi-stage build with golang-image base
- `go.mod` - Go dependencies

## Testing

- Unit tests: `/go:cmd-test ./...`
- Integration tests: Require Portainer instance running
- MCP connectivity: `/mcp:cmd-test portainer-mcp`
- Docker build: `docker build .`

## Deployment

1. Build and push Docker image to registry
2. Update corresponding Helm chart with new image tag
3. Register in `.mcp.json`: `/mcp:cmd-add portainer-mcp <url>`
4. Deploy via ArgoCD

## Configuration

Environment variables:

- `PORTAINER_URL` - Portainer instance URL
- `PORTAINER_API_TOKEN` - Portainer API authentication token
- `PORTAINER_ENVIRONMENT_ID` - Default environment ID (optional)
- `MCP_SERVER_PORT` - MCP server listening port (default: 8080)
