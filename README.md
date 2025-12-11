name: Python CI

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Source Code
      uses: actions/checkout@v3

    - name: Setup Python
      uses: actions/setup-python@v4
      with:
        python-version: "3.11"

    - name: Install Dependencies
      run: |
        python -m pip install --upgrade pip
        pip install pytest

    - name: Run Tests
      run: pytest
