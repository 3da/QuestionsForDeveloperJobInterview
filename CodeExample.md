# C#


## 1

```C#
public string ReadFirstLine(string path)
{
    var file = new StreamReader(path);
    return file.ReadLine();
}

```




## 2

```C#
if (result < 3)
    return true;
else
    return false;

```


## 3

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

## 4

```C#
public Task<string> ReadFirstLine(string path)
{
    using (var file = new StreamReader(path))
    {
        return file.ReadLineAsync();
    }
}

```

## 5

```C#
public void Process()
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
