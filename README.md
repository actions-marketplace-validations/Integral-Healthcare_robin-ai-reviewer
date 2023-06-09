# Robin AI

<img src="/assets/robin.png" alt="Robin watercolor image" style="width: 200px; height: 200px;"/>

Named after Batman's assistant, Robin AI is an open source Github project that automatically reviews Github pull requests, providing a letter grade from A to F, suggested improvements, and sample code for improvement.

## Demo

![Demo video](/assets/demo.gif)

## Arguments

| Name                | Required | Default Value             | Description                                                                                                       |
|---------------------|----------|---------------------------|-------------------------------------------------------------------------------------------------------------------|
| `GITHUB_TOKEN`      | Yes      | Automatically supplied    | A Github access token with the `repo` and `pull_request` scopes.                                                  |
| `OPEN_AI_API_KEY`   | Yes      | N/A                       | An API key from Open AI's developer portal.                                                                       |
| `gpt_model_name`    | No       | `gpt-3.5-turbo-0301`      | The name of the GPT model to use for text generation.                                                             |
| `github_api_url`    | No       | `https://api.github.com`  | The URL for the Github API endpoint. (Only relevant to enterprise customers.)                                               |

## Installation

To use Robin AI in your Github project, you'll need to add it as a Github action. Here's how:

1. In your Github repository, navigate to the "Actions" tab.
2. Click on the "New workflow" button.
3. Select the option to "Set up a workflow yourself".
4. Copy and paste the following code into the new file:

```yml
name: Robin AI Reviewer

on: [pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3
      - name: Robin AI Reviewer
        uses: Integral-Healthcare/robin-ai-reviewer@v[INSERT_LATEST_RELEASE]
        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          OPEN_AI_API_KEY: ${{ secrets.OPEN_AI_API_KEY }}
```

5. Save the file with a name like `robin.yml`.
6. Create a secret in your Github repository called `OPEN_AI_API_KEY` and set it to the value of your Open AI API key.

With those steps complete, Robin AI will automatically run every time a pull request is opened or edited in your Github repository.

## Usage

When Robin AI runs, it will post a comment on the pull request with its letter grade, suggested improvements, and sample code for improvement. You can use this information to improve the quality of your code and make your pull requests more likely to be accepted.

## Performance
Great emphasis has been put on ensuring a performant runtime.

| Metric         | Value     |
|----------------|-----------|
| Docker Image Size  | 18.5MB   |
| Average Action Runtime | 14s |

The Docker image for Robin AI has a size of 18.5MB, which is relatively small and should be quick to download and use. On average, the Robin AI Github action runtime is 14 seconds, which means that it should be able to process pull requests quickly and efficiently. These metrics may vary depending on factors such as the size and complexity of the code being reviewed, the speed of the internet connection, and the availability of Open AI's API.

## Contributing

If you'd like to contribute to Robin AI, we welcome your input! Please feel free to submit issues or pull requests on our Github repository.

## License

Robin AI is licensed under the MIT License. See `LICENSE` for more information.
