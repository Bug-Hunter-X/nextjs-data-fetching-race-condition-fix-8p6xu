# Race Condition in Next.js 15 Data Fetching

This repository demonstrates a race condition that can occur in Next.js 15 when using `getStaticProps` or `getServerSideProps` with multiple asynchronous data fetching operations.  The bug and solution are presented with code examples for clarity.

## Bug Description

When fetching data from multiple sources asynchronously, there's a risk that one operation might complete before another, leading to inconsistencies. This is especially problematic if these values are used in conjunction with each other. The example uses two API calls where the second is dependent on the response of the first.  If the second call completes before the first, an error results.  This error is not necessarily obvious but results in incorrect data presentation on the page.

## How to Reproduce

1. Clone the repository.
2. Install dependencies: `npm install`
3. Run the development server: `npm run dev`
4. Observe the potential error in the console and page content.

## Solution

The solution involves using `Promise.all` to ensure all data fetching operations complete before proceeding. This prevents race conditions and maintains data integrity.