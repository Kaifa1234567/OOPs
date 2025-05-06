To create an Object-Oriented Programming (OOP) code structure that fetches GitHub repository details, you can use Python and its requests module for accessing the GitHub API. Here's a basic but well-structured example using OOP:


---

Python OOP Code to Fetch GitHub Repository Details

import requests

class GitHubRepo:
    def __init__(self, owner, repo):
        self.owner = owner
        self.repo = repo
        self.base_url = f"https://api.github.com/repos/{owner}/{repo}"

    def fetch_details(self):
        response = requests.get(self.base_url)
        if response.status_code == 200:
            return response.json()
        else:
            raise Exception(f"Error fetching data: {response.status_code}")

    def display_details(self):
        try:
            data = self.fetch_details()
            print(f"Repository: {data['full_name']}")
            print(f"Description: {data.get('description', 'No description')}")
            print(f"Stars: {data['stargazers_count']}")
            print(f"Forks: {data['forks_count']}")
            print(f"Open Issues: {data['open_issues_count']}")
            print(f"URL: {data['html_url']}")
        except Exception as e:
            print(e)

# Example usage
if __name__ == "__main__":
    repo = GitHubRepo("octocat", "Hello-World")
    repo.display_details()


---

How This Uses OOP Principles

Encapsulation: The class encapsulates all behavior and data related to the repository.

Abstraction: Users call display_details() without needing to know the internals of the API call.

Reusability: You can create multiple instances for different repositories easily.
