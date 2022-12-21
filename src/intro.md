# Introduction

Chatoy is an instant messenger.

## Structure

Chatoy client is structured into the core implemented in C++ and the cross-platform UI implemented in Java, and these two parts interact via JNI.

Chatoy server is implemented in Rust, using SQLite as the database.
