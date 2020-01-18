# C#

## 1
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






## 2
```C#
if (result < 3)
       return true;
else
       return false;

```

## 3
```C#
public string ReadFirstLine(string path)
{
  var file = new StreamReader(path);
  return file.ReadLine();
}
```
