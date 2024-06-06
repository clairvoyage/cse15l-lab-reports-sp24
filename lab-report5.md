# Part 1

# 1. Failing one test for addition method, help?

I am writing a method to add all the integers in an array of integers. My method seems to work for the most part, but it’s been failing one of the tests, and I’m not sure why. Here’s the method:

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczOjB65cMVg9Mm4Y2glXaJW3HvqBaQ-tPS_pouLcj5-q1lfDg9Pd9ejpopAWlj4FAp8E1VkGi-c9HDSPLwbB5PZXbtMpqdhkZfufDoT4mWjBppprV_4Br3XOUGl2ahWPn7aYznXN4ao1X8R3rsLkeGia=w1270-h520-s-no?authuser=0)

And here’s my tests:

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczOZY8DzTEDwI0G_JIH-PpVN8QRHS9P-j8hhfDcc77eYBWud4-pIWUK-uG6M6BcoaM-XfJwNxGlehIykwhzw3-M4XpsKFAZpHyVgA7RBdQQpwJQKqb3MjfvVPzr748_gFxxV3nQTKjBqgNiubOuGjv8A=w1438-h994-s-no?authuser=0)

This is the message I get from doing the test:

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczMnlri4rACK-ZbMifq_x4xV2McpAErc2TeOfNZm5cWGuVBg1XG5byCh6OrmklTAG2IL-Y7TjUKY0mV5_B3TXtflZuobfW7EAL8so7X7ww_yaIb29CiHjQSjG9C902WmgKNbQOqon_8JqQj8-WDKcRiF=w1272-h746-s-no?authuser=0)

It looks like something in my addition was slightly off as all my other tests passed, and this one was only off by 1. I’m not sure if this has something to do with Java being weird about adding numbers or an issue on my part.

# 2. TA’s response

It seems there could be an issue with the number that was initialized to be the total at the start of the adding method. Could you check what the initial value of the `total` variable is?

# 3. Trying the suggestion

I tried using jdb to find the value of `total` before the loop. To make things easier, I used this bash script:

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczPy2AC1o5nndTfo6T-D2tjXjPQa2HriPzpfb5QjiFlPi9cltR3LOuFzvLLPYIqrERhP_ymWOaZ9wvtJmleeVBgyxQ6OeGRGNxUuB25-zEEGs_-RdAU4Z8YlGnoNeyFr7-MXEYy_pPSOTYZXeIh-93tN=w1514-h182-s-no?authuser=0)

It looks like here, `total` is set to 0 before the loop. I’m pretty sure that would be the right value for it at this point.

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczMBMjFRwht4mWusAc_DZcoyCFlnYBcBdXIgz-gglnNth1EKLd3Y4u216AQCVo-X5fVRlMb9I-SaLUJNqe020ai6wlAJgeWECe6MES9G7x2PWyS0FsHQzt-jGHYJf6jzD3W9nmUAzxKKB6KKmCGJTvpu=w1120-h994-s-no?authuser=0)

I then realized that this is the value of `total` in the first test. The second test was the one that was failing, so I set the breakpoint at the same spot again to check the value of `total` before the loop in the second test. Surely enough, I got an initial total value of 1. 

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczNpDHK45Ui5ptAccW5yyodvUChXTprd91pKcIbGGdneeg64Msyd31ceXBj7ohEqOzsYUrzLMukiMtqrYf3aDcv9weS7itxy_LsLXACMDUxzw2OOSNcrA3ErVFLrYjiCrMNGRLQANlssqUEIjDv3gm7k=w1466-h994-s-no?authuser=0)

I stepped through the loop several more times for this test and found that the method adds 1+1+2+3 to get a total of 7. It seems to be adding the first element twice.

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczNGTDIzbrdfTi8riK7lAoYgMETkKZxvI0NirJPg-x15syFrE9KV_lHwrApapvij0VrHr86RQMiSA7gDgPQ2Xvy7pT4IDz1LWZmmDjO1TSFFlUSL57evR22t5JIl2ehoCZO4HA1BAtiD_JwYnI0_h9NP=w748-h994-s-no?authuser=0)

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczNKfSeNNjCi4rnxfaibMjCwpbTG5Eklhii_wxHBig3ShVP9BGppPtnMWyvo6vFVcq36uvz0u0gF9oXYTKjsMnWr0Wet3Q7FvyR7YpmH_IaKtDlxrnwzqW_0VaJCYD8eyeAUOUWAmoS9KcwlKszc8tC7=w936-h694-s-no?authuser=0)

# 4. All information

## File and directory structure:

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczMCumX_4WBQLEI8E43H3kbWi1SBLVX2mclk0p167G0PXFbe4BrhsoVsnt0fE8dwrD91yqgv6rloHZtDmoK1dvxplwZRdCYPo6TJ6w4h_Op2bazZQlJhFmMG2kB3LuNVJdu5byW1by_zLXjE79NlYz7C=w766-h940-s-no?authuser=0)

## Contents of each file before:

`Testers.java`

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczOB4WvSQ-Y4sJku7GD_yNUkaBjLz-U760fKA3CZCrViYvxFiDak-ygQ1i5zBBUO6bHQQhvW-kalYde5Ey1jcwwho_Nt32QF-17NKS5Nl9uw3h2aprdkiTlW8tEKMFzn2sc0_SfAWISAFVewGzNHXA__=w1030-h994-s-no?authuser=0)

`test.sh`

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczNEDjdUJ1oGIR-NhaWV-1tBfQn0taOIlCM2safd211_uUlrx2hs-YgGd4UqlBdSxH1C80zgj95Rb1aW6W_OA0ZkbBjMA0wDme13xSzPBG3GVvznEz6KYN6mxKhl7mpb4FjwSjFh7h6uDL7Qv1LfyXIH=w1514-h252-s-no?authuser=0)

`AddAll.java`

![Untitled](https://lh3.googleusercontent.com/pw/AP1GczMI-CwMW7WUGNe5WHadNUG591dKR5KNxYQlcurR9_p2zSUHVX0dRRf-cVfkBMzdHslIo4yRyfwJiPO-1BW-bNY7hqQa6EIlHKVRJ1MjrDtRTDill1rOkMgsoGoxQT7E2Su4N_s0GuXT9f_eFd8dBbPl=w1364-h626-s-no?authuser=0)

## Command lines to trigger the bug:

1. Run test.sh
2. The output at the terminal will indicate that 1 out of the 3 tests failed. The expected value, 6, is different from the actual value, 7.

## Description of how to fix the bug:

Line 3 in [`AddAll.java`](http://AddAll.java) initializes the value of `total` to be the first element in the array. Later in the loop, that same first element is added again to the array. To fix the bug, change the initial value of `total` in line 3 of `AddAll.java` from `array[0]` to `0` to avoid adding the first element twice. 

---

# Part 2

One thing I learned during the second half of this quarter is how to use the debugger. My mom is a software developer, and she tried to show me how to use the debugger once. I got so intimidated I didn’t continue learning how to use it. I’m glad I finally got to learn to use the debugger in a practical way.
