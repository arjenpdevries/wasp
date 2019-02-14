# Adding a list of URLs to the index

Create a file with the URLs to add, one per line.

Issue:

    wget -p -q -e use_proxy=yes -e http_proxy=127.0.0.1:8001 -e https_proxy=127.0.0.1:8001 --ca-certificate /home/user/srv/warcprox/warcprox-ca.pem --delete-after -i urls.txt

Explanation:

+ `-p` ensures page requisites (images, css, etc.) are also downloaded;
+ `-q` quiet (`-nv` would be a good alternative to monitor progress);
+ `-e use_proxy=yes` and the two `-e http_proxy=127.0.0.1:8001 -e https_proxy=127.0.0.1:8001` route the downloads via the WASP proxy, triggering indexing by WASP;
+ `--ca-certificate /home/user/srv/warcprox/warcprox-ca.pem` ensures that HTTPS requests are correctly "attacked" so they can be stored in the personal web archive;
+ `--delete-after` tells `wget` to delete the files (as they are archived by WASP already);
+ `-i [filename]` provides the list of URLs to crawl.
