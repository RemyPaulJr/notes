Baseline Performance
- automatically scales to high request rates, latency 100-200ms
- your application can achieve at least 3500 PUT/COPY/POST/DELETE or 550 GET/HEAD requests per second per prefix in a bucket
- there are no limits to the number of prefixes in a bucket
- Example:
	- object path --> prefix
		- bucket/folder/sub/file --> folder/sub
		- you get 3500 put and 5500 get for this prefix

Performance
- Multi-Part upload:
	- recommended for files > 100MB, must use for files > 5GB
	- can help parallelize uploads (speed up transfers)
- Transfer Accerlation
	- Increase transfer speed by transfer