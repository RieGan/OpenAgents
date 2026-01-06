# BTCA Context Specialist - Evaluation Tests

## Overview

**Agent:** `subagents/utils/btca-context`  
**Parent Agent:** `openagent`  
**Description:** Secure, high-performance context gathering using BTCA (Better Context App) with intelligent caching and graceful fallback strategies

## Test Structure

```
utils/btca-context/
├── config/
│   └── config.yaml          # Test configuration
├── tests/
│   ├── smoke-test.yaml      # Basic sanity check
│   ├── resource-management.yaml  # Resource operations
│   ├── caching.yaml         # Cache behavior
│   └── error-handling.yaml  # Error scenarios
└── README.md               # This file
```

## Running Tests

### Standalone Mode
Tests the subagent directly (forces `mode: primary`):

```bash
# Using npm
npm run eval:sdk -- --subagent=utils-btca-context

# Using Makefile
make test-subagent SUBAGENT=utils-btca-context

# Verbose output
npm run eval:sdk -- --subagent=utils-btca-context --verbose
```

### Delegation Mode
Tests via parent agent (real-world usage):

```bash
# Using npm
npm run eval:sdk -- --subagent=utils-btca-context --delegate

# Using Makefile
make test-subagent-delegate SUBAGENT=utils-btca-context
```

## Test Suites

### Smoke Tests
- **Purpose:** Basic sanity checks
- **Coverage:** Agent initialization, tool verification, basic functionality
- **Status:** ✅ Implemented

### Resource Management Tests
- **Purpose:** Test BTCA resource operations
- **Coverage:** Resource checking, adding, removal, validation
- **Status:** 🚧 TODO

### Caching Tests
- **Purpose:** Verify cache behavior and performance
- **Coverage:** Cache storage, retrieval, TTL, cleanup
- **Status:** 🚧 TODO

### Error Handling Tests
- **Purpose:** Test error scenarios and recovery
- **Coverage:** BTCA unavailable, network errors, invalid commands
- **Status:** 🚧 TODO

## Test Environment Setup

### Prerequisites
1. BTCA CLI installed and available in PATH
2. Network connectivity for repository cloning
3. Write permissions in `.tmp` directory for cache
4. Valid git repositories for testing

### Test Data
Test cases use mock technologies and repositories:
- React (https://github.com/facebook/react)
- Vue.js (https://github.com/vuejs/core)  
- Common patterns and questions
- Error scenarios and edge cases

## Adding Tests

1. Create test file in `tests/` directory
2. Follow the YAML schema from `evals/agents/shared/tests/golden/`
3. Add appropriate tags: `subagent`, `utils-btca-context`, suite name
4. Update this README with test description

## Test Scenarios

### Security Testing
- Command validation and injection prevention
- Permission enforcement for dangerous operations
- Input sanitization and argument separation
- Audit logging verification

### Performance Testing
- Cache hit/miss ratios
- Response time measurements
- Resource usage monitoring
- Concurrent operation handling

### Integration Testing
- Delegation from parent agents
- Context file handling
- Registry integration
- Profile compatibility

## Expected Outcomes

### Functional Requirements
- All BTCA commands execute securely
- Resources managed correctly
- Cache operates with 24-hour TTL
- Errors handled gracefully with alternatives

### Security Requirements
- No command injection vulnerabilities
- All external commands validated
- Proper audit logging
- Permission enforcement working

### Performance Requirements
- Response times under 30 seconds (cache hit)
- Response times under 2 minutes (cache miss)
- Cache hit rate above 70%
- Memory usage within limits

## Troubleshooting

### Common Issues

**BTCA Not Found**
```bash
# Check installation
which btca

# Install if missing
bun add -g btca
```

**Permission Errors**
```bash
# Check cache directory permissions
ls -la .tmp/btca-cache/

# Create if missing
mkdir -p .tmp/btca-cache
```

**Network Connectivity**
```bash
# Test repository access
git ls-remote https://github.com/facebook/react

# Check internet connection
curl -I https://api.github.com
```

## Related Documentation

- [Subagent Testing Guide](../../../SUBAGENT_TESTING.md)
- [Eval Framework Guide](../../../README.md)
- [Agent Source](../../../../.opencode/agent/subagents/utils/btca-context.md)
- [BTCA Documentation](https://btca.dev)