---
title: 'レッスン 2 : スナップショット フォルダーの準備 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f286cde9-c0d0-43ef-b7ba-53c3cbb8906c
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 5ec45b0a29f9f4c8fb1e6a9b683e47797f194885
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62721021"
---
# <a name="lesson-2-preparing-the-snapshot-folder"></a>レッスン 2 : スナップショット フォルダーの準備
  このレッスンでは、パブリケーション スナップショットの作成と保存に使用されるスナップショット フォルダーを設定する方法を学習します。  
  
### <a name="to-create-a-share-for-the-snapshot-folder-and-assign-permissions"></a>スナップショット フォルダーの共有を作成し、アクセス許可を与えるには  
  
1.  Windows エクスプローラーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ フォルダーに移動します。 既定の場所は、C:\Program Files\Microsoft SQL Server\MSSQL.X\MSSQL\Data です。  
  
2.  
  **repldata**という名前の新しいフォルダーを作成します。  
  
3.  このフォルダーを右クリックし、 **[プロパティ]** をクリックします。  
  
4.  
  **[repldata のプロパティ]** ダイアログ ボックスの **[共有]** タブで、 **[共有]** をクリックします。  
  
5.  
  **[ファイルの共有]** ダイアログ ボックスで、 **[共有]**、 **[完了]** の順にクリックします。  
  
6.  
  **[セキュリティ]** タブで、 **[編集]** をクリックします。  
  
7.  
  **[アクセス許可]** ダイアログ ボックスで **[追加]** をクリックします。 **[ユーザー、コンピューター、サービスアカウント、またはグループの選択**] ボックスに、レッスン1で作成したスナップショットエージェントアカウントの名前を\< _Machine_Name>_ **\ repl_snapshot**とし\<て入力します。ここで*Machine_Name*>はパブリッシャーの名前です。 [**名前の確認**]、[**OK**] の順にクリックします。  
  
8.  前の手順を繰り返して、 \<ディストリビューションエージェントのアクセス許可を追加します。 _Machine_Name>_ **\ repl_distribution**、マージエージェント\<Machine_Name **\>**_として追加_します。  
  
9. 次のアクセス許可が与えられていることを確認します。  
  
    -   repl_snapshot - フル コントロール  
  
    -   repl_distribution - 読み取り  
  
    -   repl_merge - 読み取り  
  
10. 
  **[OK]** をクリックして **[repldata のプロパティ]** ダイアログ ボックスを閉じると、repldata 共有フォルダーが作成されます。  
  
## <a name="next-steps"></a>次の手順  
 ここでは、スナップショット フォルダーの共有を構成しました。 次は、ディストリビューションを構成します。 「 [レッスン 3: ディストリビューションの構成](lesson-3-configuring-distribution.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [スナップショットフォルダーをセキュリティで保護する](security/secure-the-snapshot-folder.md)  
  
  
