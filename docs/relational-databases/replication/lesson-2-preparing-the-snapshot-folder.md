---
title: "レッスン 2 : スナップショット フォルダーの準備 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f286cde9-c0d0-43ef-b7ba-53c3cbb8906c
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f9b63fa28f53724adce16bedda14e11cd3a750b8
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="lesson-2-preparing-the-snapshot-folder"></a>レッスン 2 : スナップショット フォルダーの準備
このレッスンでは、パブリケーション スナップショットの作成と保存に使用されるスナップショット フォルダーを設定する方法を学習します。  
  
### <a name="to-create-a-share-for-the-snapshot-folder-and-assign-permissions"></a>スナップショット フォルダーの共有を作成し、アクセス許可を与えるには  
  
1.  Windows エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ フォルダーに移動します。 既定の場所は、C:\Program Files\Microsoft SQL Server\MSSQL.X\MSSQL\Data です。  
  
2.  **repldata**という名前の新しいフォルダーを作成します。  
  
3.  このフォルダーを右クリックし、 **[プロパティ]**をクリックします。  
  
4.  **[repldata のプロパティ]** ダイアログ ボックスの **[共有]** タブで、 **[共有]**をクリックします。  
  
5.  **[ファイルの共有]** ダイアログ ボックスで、 **[共有]**、 **[完了]**の順にクリックします。  
  
6.  **[セキュリティ]** タブで、 **[編集]**をクリックします。  
  
7.  **[アクセス許可]** ダイアログ ボックスで **[追加]**をクリックします。 **[選択するオブジェクト名を入力してください]** ボックスに、レッスン 1 で作成したスナップショット エージェント アカウントの名前「\<*コンピューター名>***\repl_snapshot**」を入力します (\<*コンピューター名>* はパブリッシャーの名前)。 **[名前の確認]**をクリックして、 **[OK]**をクリックします。  
  
8.  前の手順を繰り返して、ディストリビューション エージェント (\<*コンピューター名>***\repl_distribution**) とマージ エージェント (\<*コンピューター名>***\repl_merge**) のアクセス許可を追加します。  
  
9. 次のアクセス許可が与えられていることを確認します。  
  
    -   repl_snapshot - フル コントロール  
  
    -   repl_distribution - 読み取り  
  
    -   repl_merge - 読み取り  
  
10. **[OK]** をクリックして **[repldata のプロパティ]** ダイアログ ボックスを閉じると、repldata 共有フォルダーが作成されます。  
  
## <a name="next-steps"></a>次の手順  
ここでは、スナップショット フォルダーの共有を構成しました。 次は、ディストリビューションを構成します。 「 [レッスン 3: ディストリビューションの構成](../../relational-databases/replication/lesson-3-configuring-distribution.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[スナップショット フォルダーのセキュリティ保護](../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  
  
  

