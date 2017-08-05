# IRC Commands Reference

## Associate your phone number with your alias

### Command

```
voip: <last 3 digits of SIP/...> is <alias>
```

### Example

Suppose your alias is `kimhd` and phone number is 555-222-1212. Look for your phone number in the chat window and get the last 3 digits from the adjacent string `[SIP/xx.xx.xx.xxx-xxxxxxxx]`

```
[09:01] <voip-vctf> 15552221212 [SIP/69.77.77.777-00000174] has joined the conference.
```

The last 3 digits are `174`. You would enter command:

```
voip: 174 is kimhd
```

## Speaking off the record

### Command

```
/me <your message>
```

### Example

```
/me can you speak up please?
```

## List connections

### Command

```
voip: connections?
```

## Scribing

### Command

```
<alias>: <what they said>
```

### Example

Suppose ChristopherA is scribing, and kimhd says "The next thing we will discuss is the DID spec"

ChristopherA would type:
```
kimhd: The next thing we will discuss is the DID spec
```

To continue, and avoid repeating the author name, type `...` (on the new line)

## Posting an agenda

### Command

```
Agenda: <agenda link>
```

### Example

```
Agenda: https://lists.w3.org/Archives/Public/public-credentials/2017Jul/0040.html
```
