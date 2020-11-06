# How to contribute to the Carnalitas Framework

## You want to add a new feature or bugfix

In order to keep the development branch stable, you should not commit directly to it. Here is the workflow you should follow:

### Create a new branch

If you are an official contributor to this project, **create a new branch** from the "developing" branch (you can do it from github or directly from your local git repository)
> If you are not an official contributor, you can fork this project and work on your feature there

- It is recommended to name your branch "**feature/concise-name-of-the-feature**" for a new feature or "**fix/concise-name-of-the-bugfix**" for a bugfix.

### Work on your branch

You can now start working on your feature by pushing your modification to your feature branch.

- Only add changes that are related to that feature
- Create new files rather than writing into existing ones
- Use as specific of a namespace as possible to avoid awkward conflicts

### Create a pull request

Once your feature is done, or at least stable and functioning (doesn't cause crashes or break existing stuff), you can **create a pull request** from your feature branch to the development branch

- Follow the template instructions
- Add a reviewer to the pull request (cherisong and potentially another contributor who already worked on the code you are modifying)
- Add the label "enhancement" and any other relevant label, like "visual" if you made some graphical modification
- If your feature or bugfix is supposed to close or fix an existing issue, please link it in the pull request (the option is also in the right-hand column)

## Adding new translations

**Note: Only do this just before a final release**

Translations go into the `localization` folder where each language gets its own sub directory. You can use the localization helper to quickly setup a new language (requires [Python](https://www.python.org/)):

In a terminal (shell, cmd, powershell...), execute the following command

```shell
python localization_helper.py update --lang <language>
```

Where `<language>` is the name of the language you want to translate to, eg: `german`.

Before running the script, make sure that all the strings already translated are in the format `key:1 "value"`. The `:1` tells the script that this line is already translated and thus should not be changed.
The script will then add all the missing strings, in english, and with the format `key:0 "value"`.

**Important:** Once you have translated a string, do not forget to replace the `:0` by a `:1`. Every string with a different format than `key:1 "value"` will be replaced by the english value when you run the script

If you want to see translation statistics use `python localization_helper.py stats`.
