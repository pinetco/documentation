# Cleanup Open Replays Storage

- Read guidelines to cleanup storage from here: [Docs](https://docs.openreplay.com/en/configuration/cleanup-storage)
- First remove sessions from postgresql which takes the most space
  - Follow the guidelines to start postgresql session: [Docs](https://docs.openreplay.com/en/configuration/cleanup-storage/#database-postgesql)
  - Run this query to delete older sessions by replacing the date
    ```postgresql
    DELETE FROM public.sessions WHERE start_ts < extract(epoch from '2023-01-01'::date) * 1000;
    ```
  - Postgresql takes some hours to release space by vacuuming, but we can force it instantly by running this query. (It will take some time to execute)
    ```postgresql
    VACUUM FULL;
    ```
- Then remove older recordings by following the guidelines [Docs](https://docs.openreplay.com/en/configuration/cleanup-storage/#recordings)
