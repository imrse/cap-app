## Overview

This repository contains a sample Capacitor JS application featuring a Vimeo player embedded within a Vue component. The purpose of this repo is to demonstrate an issue where Vimeo player events are not correctly emitted in WKWebView as of 2024-05-16. While videos load successfully, the expected Vimeo video events do not trigger properly inside WKWebView.

## Details

- **Framework**: Capacitor JS
- **Component**: Vue
- **Issue Date**: 2024-05-16

## Problem Description

- **Environment**: WKWebView
- **Issue**: Vimeo player events are not being emitted as expected.
- **Impact**: Although videos load, no Vimeo video events are emitted correctly within the WKWebView environment.

## Demonstration

State flags under the video player indicate if the player has received the "ready" and "play" events:
- **Ready Event**: Indicates if the player has received the "ready" event.
- **Play Event**: Indicates if the player has received the "play" event.

### Browser Environment

Event emissions work correctly in a browser environment, such as Safari and Chrome. This can be demonstrated by starting the development web server and accessing the application via a browser.

### iOS Simulator

In contrast, using the iOS simulator in Xcode, the event emissions do not work. This difference highlights the issue with WKWebView in the iOS environment.

## How to Set Up for Browser App Where Events Work

1. Install dependencies:
    ```sh
    npm install
    ```

2. Start the development server:
    ```sh
    npm run serve
    ```

## How to Set Up for Native App Where Events Don't Work

Check the requirements for iOS development at [CapacitorJS Environment Setup](https://capacitorjs.com/docs/getting-started/environment-setup).

1. Install dependencies:
    ```sh
    npm install
    ```

2. Build
    ```sh
    npm run build
    ```

3. Run the app on iOS:
    ```sh
    npx cap run ios
    ```
