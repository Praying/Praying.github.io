---
title: "在Rust的Unit Test中输出日志"
date: 2019-09-01T14:22:25+08:00
draft: true
---
先贴上单元测试的代码
```rust
#[macro_use]
use crate::core::logger;
#[test]
fn test_logger() {
    assert_eq!(logger::init(logger::LoggingLevel::Debug), true);
    launch_info!("Hello logger");
    launch_info!("Hello World");
    debug_!("Hello, Debug");
}
```
使用 

>cargo test 

运行测试代码时，测试通过，但是没有日志输出。然后在Reddit看到，应该用下面这条命令

> cargo test -- --nocapture

- [Reddit链接](https://www.reddit.com/r/rust/comments/7up0bm/show_logging_output_during_test_runs/
)
