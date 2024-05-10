---
title: Test Case Format
created: 2024-05-10 15:11
last modified: Friday 10th May 2024 15:11:45
Aliases:
Tags:

---
# Test Case Entry Structure

All our test cases are recorded in the form of a table

## Basic Fields 

All tables have basic fields:
- `id` - unique identifier
- `priority` - Priority: Highest | High | Medium | Low | Lowest
- `title` - Title
- `preconditions` - Preconditions for executing the test case
- `steps to reproduce` - Steps to reproduce the test case
- `expected result` - Expected result
- `status` - Status: **Pass** | **Fail** | **Dev**

Also, unique fields can be added for individual elements

## Groups and Subgroups

### Groups

**All test cases must belong to some group**

A group represents some test cases that belong to one large functionality. For example, presence check. This is a large group

Group declaration - a line in the table, with a blue background. All test cases that go below are test cases of this group.

The group id is recorded without numbers

Group test cases have the name `{group name}-{number}`, where `number` is the serial number of the test case

### Sub-groups

We may not have enough just groups and we may want to create sub-groups.

The declaration of a sub-group is a line in the table, with a yellow color. All test cases that go below are test cases of this sub-group.

The id of the sub-group is written as the name `{group name}-{number}`, where `number` is the serial number of the sub-group

The test cases of the sub-group have the name `{sub group name}.{number}`, where `number` is the serial number of the test case

## Examples

Example of a group and sub-group:

![[Pasted image 20240510152317.png]]

Example of only groups without sub-groups:

![[Pasted image 20240510152341.png]]
