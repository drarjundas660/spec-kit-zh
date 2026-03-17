---

description: "Task list template for feature implementation"
---

# 任务列表：[功能名称]

**输入**：来自 `/specs/[###-feature-name]/` 的设计文档
**前置条件**：plan.md（必需）、spec.md（用户故事必需）、research.md、data-model.md、contracts/

**测试**：下面的示例包含测试任务。测试是可选项，只有在功能规格中明确要求时才应包含。

**组织方式**：任务按用户故事分组，以便每个故事都能独立实现和测试。

## 格式：`[ID] [P?] [Story] 描述`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (e.g., US1, US2, US3)
- Include exact file paths in descriptions

## 路径约定

- **Single project**: `src/`, `tests/` at repository root
- **Web app**: `backend/src/`, `frontend/src/`
- **Mobile**: `api/src/`, `ios/src/` or `android/src/`
- Paths shown below assume single project - adjust based on plan.md structure

<!-- 
  ============================================================================
  IMPORTANT: The tasks below are SAMPLE TASKS for illustration purposes only.
  
  The /speckit.tasks command MUST replace these with actual tasks based on:
  - User stories from spec.md (with their priorities P1, P2, P3...)
  - Feature requirements from plan.md
  - Entities from data-model.md
  - Endpoints from contracts/
  
  Tasks MUST be organized by user story so each story can be:
  - Implemented independently
  - Tested independently
  - Delivered as an MVP increment
  
  DO NOT keep these sample tasks in the generated tasks.md file.
  ============================================================================
-->

## 阶段 1：准备工作（共享基础设施）

**目的**：项目初始化与基础结构准备

- [ ] T001 按实施计划创建项目结构
- [ ] T002 使用 [framework] 依赖初始化 [language] 项目
- [ ] T003 [P] 配置 lint 与格式化工具

---

## 阶段 2：基础能力（阻塞性前置条件）

**目的**：任何用户故事开始前都必须完成的核心基础设施

**关键说明**：在本阶段完成前，不得开始任何用户故事实现

Examples of foundational tasks (adjust based on your project):

- [ ] T004 搭建数据库 Schema 与迁移框架
- [ ] T005 [P] 实现认证与授权框架
- [ ] T006 [P] 搭建 API 路由与中间件结构
- [ ] T007 创建所有故事共同依赖的基础模型/实体
- [ ] T008 配置错误处理与日志基础设施
- [ ] T009 搭建环境配置管理

**检查点**：基础能力已就绪，用户故事实现现在可以并行展开

---

## 阶段 3：用户故事 1 - [标题]（优先级：P1）

**目标**：[简要说明该故事交付的内容]

**独立测试**：[如何独立验证该故事]

### 用户故事 1 的测试（可选，仅在明确要求测试时填写）

> **NOTE: Write these tests FIRST, ensure they FAIL before implementation**

- [ ] T010 [P] [US1] 在 `tests/contract/test_[name].py` 中为 [endpoint] 编写契约测试
- [ ] T011 [P] [US1] 在 `tests/integration/test_[name].py` 中为 [用户旅程] 编写集成测试

### 用户故事 1 的实现

- [ ] T012 [P] [US1] 在 `src/models/[entity1].py` 中创建 [Entity1] 模型
- [ ] T013 [P] [US1] 在 `src/models/[entity2].py` 中创建 [Entity2] 模型
- [ ] T014 [US1] 在 `src/services/[service].py` 中实现 [Service]（依赖 T012、T013）
- [ ] T015 [US1] 在 `src/[location]/[file].py` 中实现 [endpoint/feature]
- [ ] T016 [US1] 增加校验与错误处理
- [ ] T017 [US1] 为用户故事 1 的操作增加日志

**检查点**：到此为止，用户故事 1 应可独立运行并完成测试

---

## 阶段 4：用户故事 2 - [标题]（优先级：P2）

**目标**：[简要说明该故事交付的内容]

**独立测试**：[如何独立验证该故事]

### 用户故事 2 的测试（可选，仅在明确要求测试时填写）

- [ ] T018 [P] [US2] 在 `tests/contract/test_[name].py` 中为 [endpoint] 编写契约测试
- [ ] T019 [P] [US2] 在 `tests/integration/test_[name].py` 中为 [用户旅程] 编写集成测试

### 用户故事 2 的实现

- [ ] T020 [P] [US2] 在 `src/models/[entity].py` 中创建 [Entity] 模型
- [ ] T021 [US2] 在 `src/services/[service].py` 中实现 [Service]
- [ ] T022 [US2] 在 `src/[location]/[file].py` 中实现 [endpoint/feature]
- [ ] T023 [US2] 与用户故事 1 的组件集成（如需要）

**检查点**：到此为止，用户故事 1 和 2 都应可独立工作

---

## 阶段 5：用户故事 3 - [标题]（优先级：P3）

**目标**：[简要说明该故事交付的内容]

**独立测试**：[如何独立验证该故事]

### 用户故事 3 的测试（可选，仅在明确要求测试时填写）

- [ ] T024 [P] [US3] 在 `tests/contract/test_[name].py` 中为 [endpoint] 编写契约测试
- [ ] T025 [P] [US3] 在 `tests/integration/test_[name].py` 中为 [用户旅程] 编写集成测试

### 用户故事 3 的实现

- [ ] T026 [P] [US3] 在 `src/models/[entity].py` 中创建 [Entity] 模型
- [ ] T027 [US3] 在 `src/services/[service].py` 中实现 [Service]
- [ ] T028 [US3] 在 `src/[location]/[file].py` 中实现 [endpoint/feature]

**检查点**：所有用户故事现在都应可独立运行

---

[Add more user story phases as needed, following the same pattern]

---

## 阶段 N：打磨与横切关注点

**目的**：影响多个用户故事的统一改进

- [ ] TXXX [P] 更新 `docs/` 中的文档
- [ ] TXXX 代码清理与重构
- [ ] TXXX 面向所有故事的性能优化
- [ ] TXXX [P] 在 `tests/unit/` 中补充单元测试（如有要求）
- [ ] TXXX 安全加固
- [ ] TXXX 运行 `quickstart.md` 验证

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: No dependencies - can start immediately
- **Foundational (Phase 2)**: Depends on Setup completion - BLOCKS all user stories
- **User Stories (Phase 3+)**: All depend on Foundational phase completion
  - User stories can then proceed in parallel (if staffed)
  - Or sequentially in priority order (P1 → P2 → P3)
- **Polish (Final Phase)**: Depends on all desired user stories being complete

### User Story Dependencies

- **User Story 1 (P1)**: Can start after Foundational (Phase 2) - No dependencies on other stories
- **User Story 2 (P2)**: Can start after Foundational (Phase 2) - May integrate with US1 but should be independently testable
- **User Story 3 (P3)**: Can start after Foundational (Phase 2) - May integrate with US1/US2 but should be independently testable

### Within Each User Story

- Tests (if included) MUST be written and FAIL before implementation
- Models before services
- Services before endpoints
- Core implementation before integration
- Story complete before moving to next priority

### Parallel Opportunities

- All Setup tasks marked [P] can run in parallel
- All Foundational tasks marked [P] can run in parallel (within Phase 2)
- Once Foundational phase completes, all user stories can start in parallel (if team capacity allows)
- All tests for a user story marked [P] can run in parallel
- Models within a story marked [P] can run in parallel
- Different user stories can be worked on in parallel by different team members

---

## Parallel Example: User Story 1

```bash
# Launch all tests for User Story 1 together (if tests requested):
Task: "Contract test for [endpoint] in tests/contract/test_[name].py"
Task: "Integration test for [user journey] in tests/integration/test_[name].py"

# Launch all models for User Story 1 together:
Task: "Create [Entity1] model in src/models/[entity1].py"
Task: "Create [Entity2] model in src/models/[entity2].py"
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Phase 1: Setup
2. Complete Phase 2: Foundational (CRITICAL - blocks all stories)
3. Complete Phase 3: User Story 1
4. **STOP and VALIDATE**: Test User Story 1 independently
5. Deploy/demo if ready

### Incremental Delivery

1. Complete Setup + Foundational → Foundation ready
2. Add User Story 1 → Test independently → Deploy/Demo (MVP!)
3. Add User Story 2 → Test independently → Deploy/Demo
4. Add User Story 3 → Test independently → Deploy/Demo
5. Each story adds value without breaking previous stories

### Parallel Team Strategy

With multiple developers:

1. Team completes Setup + Foundational together
2. Once Foundational is done:
   - Developer A: User Story 1
   - Developer B: User Story 2
   - Developer C: User Story 3
3. Stories complete and integrate independently

---

## Notes

- [P] tasks = different files, no dependencies
- [Story] label maps task to specific user story for traceability
- Each user story should be independently completable and testable
- Verify tests fail before implementing
- Commit after each task or logical group
- Stop at any checkpoint to validate story independently
- Avoid: vague tasks, same file conflicts, cross-story dependencies that break independence
