1、连接到TFS数据库服务器的tfsversioncontrol库；

2、查tbl_workspace表，找出那哥们的工作目录，

    如select * from tbl_workspace where workspacename='name'

3、利用上一步查到的workspaceid在tbl_pendingchange表中找到尚未签入的项，

    如：select * from tbl_pendingchange where workspaceid='12'

4、把这些项删除！

    如：--  delete from tbl_PendingChange where  WorkspaceId=12

 

 问题解决！

注意，在删除了tbl_pendingchange表中的数据后，还要检查一下tbl_lock表中有没有被锁定的数据。

如果有，也要一并删除。

如：--  delete from tbl_lock where  WorkspaceId=12
