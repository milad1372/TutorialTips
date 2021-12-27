https://www.toolbox.com/tech/oracle/question/how-to-release-the-lock-in-table-012003/

```
select * from dba_objects
select * from v$locked_object
select * from v$access where owner='xxx' and object='xxxx';
alter system kill session xxxx;
```
