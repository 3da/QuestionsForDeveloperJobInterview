# C#
## 1

```C#
public string GetUserNameWithEmail(User[] users)
{
    var user = users.FirstOrDefault(q => q.Email != null);
    return user.Name;
}

```

## 2

```C#
public string[] Filter(string[] words)
{
    var filtered = words.Where(w => w.Length > 5 && w.StartsWith("а"));
    _logger.LogInformation("{count}", filtered.Count());
    return filtered.ToArray();
}

```


## 3

```C#
public string ReadFirstLine(string path)
{
    var file = new StreamReader(path);
    return file.ReadLine();
}

```



## 4

```C#
if (result < 3)
    return true;
else
    return false;

```


## 5

```C#
public IEnumerable<User> Filter(IEnumerable<User> users, string email, int? minAge)
{
    return users.Where(q =>
        (q.Email == email || email == null)
        && (minAge == null || q.Age >= minAge.Value));
}

```


## 6

```C#
try
{
    //some code
}
catch (Exception ex)
{
    _logger.Error(ex);
    throw ex;
}

```

## 7

```C#
public Task<string> ReadFirstLine(string path)
{
    using (var file = new StreamReader(path))
    {
        return file.ReadLineAsync();
    }
}

```

## 8

```C#
public void Process(User[] users)
{
    var allEmails = users.Select(q => q.Email).ToArray();

    var filteredEmails = FilterBadEmails(allEmails);

    var sortedEmails = filteredEmails.OrderBy(q => q).ToArray();
    
    //some code
}

public string[] FilterBadEmails(string[] emails)
{
    return emails.Where(CheckEmail).ToArray();
}

public bool CheckEmail(string email)
{
    //some code
}

```

## 9

```C#
private readonly SemaphoreSlim _semaphore = new SemaphoreSlim(1, 1);

public async Task UpdateAsync(User user)
{
    await _semaphore.WaitAsync();

    if (!Validate(user))
    {
        throw new Exception("User is not valid")
    }
    
    //some code

    _semaphore.Release();
}

```

## 10

```C#
public bool ValidateUser(User user)
{
    return !CheckUserExist(user.Name)
        && _emailRegex.IsMatch(user.Email ?? "")
        && !string.IsNullOrWhiteSpace(user.FirstName)
        && !string.IsNullOrWhiteSpace(user.SecondName);
}
```

## 11

```C#
internal class TokenValidator
{
    string[] _tokens;

    async Task InitializeAsync()
    {
        _tokens = await File.ReadAllLinesAsync("tokens.txt");
    }

    bool CheckToken(string token)
    {
        return _tokens.Contains(token);
    }
}
```
