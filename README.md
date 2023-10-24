# Social Network Notification System

Design of a scalable and efficient notification system tailored for a social network platform.

## Table of Contents

- [Overview](#overview)
- [Components](#components)
  - [Microservices](#microservices)
  - [Notification Service](#notification-service)
  - [Real-time Notification](#real-time-notification)
  - [Final Notification Delivery](#final-notification-delivery)
  - [Infrastructure](#infrastructure)
- [Bonus Features](#bonus-features)
- [Summary](#summary)

## Overview

This document explains the system design diagram, detailing the architecture, components, and interactions of the notification system.

## Components

### Microservices

- **Microservice 1, 2, and 3**: Handle events like posts, comments, and likes.
  - **Pub/Sub Event**: Upon event generation, these services publish the event using a Pub/Sub model.

### Notification Service

- **Receiver Selection Queue**: Stores events and determines the intended recipients of notifications.
  - **Finding Receiver**: Identifies who needs to be notified based on the event.
- **Builder Queue**: Holds selected receivers and notification content.
  - **Template Builder Service**: Crafts and tailors the notification content.
- **Persistent Notification Service**: Temporarily stores the notification, awaiting delivery.
- **Notification Database**: Storing detailed notification data.

### Real-time Notification

- **Instant Notification Service**: Ensures prompt real-time notifications.
- **Instant Notification Queue**: Holds notifications ready for immediate delivery.

### Final Notification Delivery

- **Final Notification Sender Service**: Manages actual delivery.
  - **FCM & APNS**: Integrated for mobile notifications for Android and iOS devices.
  - **Web Push**: Delivers notifications to the user's browser.
- **Cache and Retry Service**: Caches undelivered notifications and retries later.

### Infrastructure

- **Load Balancer**: Distributes incoming traffic to the `Notification Service`.
- **API Gateway**: Single entry point for external services and clients.

## Bonus Features

1. **Real-time Delivery**: Ensures prompt notification delivery.
2. **Mobile Push Notification**: Supports both Android (FCM) and iOS (APNS) devices.

## Summary

The system is crafted to meet the intricate notification demands of a social networking site. It ensures timely delivery, mobile push notification support, and is designed with scalability and availability as core principles.
