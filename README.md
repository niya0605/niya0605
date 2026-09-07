name: Generate GitHub Metrics

on:
  workflow_dispatch:
  schedule:
    - cron: "0 0 * * *"

jobs:
  github-metrics:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v4

      - uses: lowlighter/metrics@latest
        with:
          filename: metrics.svg
          token: ${{ secrets.ACCESS_TOKEN }}
          user: niya0605
          template: classic
          base: header, activity, community, repositories, metadata
          config_timezone: Asia/Kolkata
