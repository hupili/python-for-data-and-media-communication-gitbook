# Computational Thinking

## Divide and conquer

### Recursion implementation

```python
students = list(range(21))
cases = list(range(5))
print('students:', students)
print('cases:', cases)

def distribute(s, c):
    if len(c) == 1:
        print('Case:', c[0], 'Students:', s)
    else:
        p = len(s) // len(c)
        print('Case:', c[0], 'Students:', s[: p])
        distribute(s[p: ], c[1: ])

distribute(students, cases)
```

Try out other number of students and cases to see if this still works.
