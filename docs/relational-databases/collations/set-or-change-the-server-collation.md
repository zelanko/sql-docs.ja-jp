---
title: サーバーの照合順序の設定または変更 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- server collations [SQL Server]
- collations [SQL Server], server
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a1aa7c772b5a204f51a863f8c22780261156929f
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35698783"
---
# <a name="set-or-change-the-server-collation"></a>サーバーの照合順序の設定または変更
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  サーバー照合順序は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスと一緒にインストールされているすべてのシステム データベースだけではなく、新しく作成したユーザー データベースの既定の照合順序になります。 サーバー照合順序は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール時に指定します。 詳細については、「 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。  
  
## <a name="changing-the-server-collation"></a>サーバー照合順序の変更  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの既定の照合順序を変更する操作は複雑で、次の手順が含まれます。  
  
-   ユーザー データベースおよびユーザー データベース内のすべてのオブジェクトを再作成するのに必要なすべての情報またはスクリプトがあることを確認します。  
  
-   [bcp ユーティリティ](../../tools/bcp-utility.md)などのツールを使用して、すべてのデータをエクスポートします。 詳細については、「[データの一括インポートと一括エクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)」を参照してください。  
  
-   すべてのユーザー データベースを削除します。  
  
-   **setup** コマンドの SQLCOLLATION プロパティで新しい照合順序を指定して、master データベースを再構築します。 例 :  
  
    ```  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName   
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]   
    /SQLCOLLATION=CollationName  
    ```  
  
     詳細については、「 [システム データベースの再構築](../../relational-databases/databases/rebuild-system-databases.md)」を参照してください。  
  
-   すべてのデータベースとデータベース内のすべてのオブジェクトを作成します。  
  
-   すべてのデータをインポートします。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの既定の照合順序を変更する代わりに、新しく作成するデータベースごとに既定の照合順序を指定することができます。  
  
## <a name="see-also"></a>参照  
 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)   
 [データベースの照合順序の設定または変更](../../relational-databases/collations/set-or-change-the-database-collation.md)   
 [列の照合順序の設定または変更](../../relational-databases/collations/set-or-change-the-column-collation.md)   
 [システム データベースの再構築](../../relational-databases/databases/rebuild-system-databases.md)  
  
  
