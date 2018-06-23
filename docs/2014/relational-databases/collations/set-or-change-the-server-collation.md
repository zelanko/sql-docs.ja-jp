---
title: サーバーの照合順序の設定または変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- server collations [SQL Server]
- collations [SQL Server], server
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
caps.latest.revision: 34
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f341ba87e716856fcad8ca2831f1fcf97f0071a5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164329"
---
# <a name="set-or-change-the-server-collation"></a>サーバーの照合順序の設定または変更
  サーバー照合順序は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスと一緒にインストールされているすべてのシステム データベースだけではなく、新しく作成したユーザー データベースの既定の照合順序になります。 サーバー照合順序は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール時に指定します。 詳細については、「 [Collation and Unicode Support](collation-and-unicode-support.md)」を参照してください。  
  
## <a name="changing-the-server-collation"></a>サーバー照合順序の変更  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの既定の照合順序を変更する操作は複雑で、次の手順が含まれます。  
  
-   ユーザー データベースおよびユーザー データベース内のすべてのオブジェクトを再作成するのに必要なすべての情報またはスクリプトがあることを確認します。  
  
-   [bcp ユーティリティ](../../tools/bcp-utility.md)などのツールを使用して、すべてのデータをエクスポートします。 詳細については、「[データの一括インポートと一括エクスポート &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md)」を参照してください。  
  
-   すべてのユーザー データベースを削除します。  
  
-   **setup** コマンドの SQLCOLLATION プロパティで新しい照合順序を指定して、master データベースを再構築します。 以下に例を示します。  
  
    ```  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName   
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]   
    /SQLCOLLATION=CollationName  
    ```  
  
     詳細については、「 [システム データベースの再構築](../databases/system-databases.md)」を参照してください。  
  
-   すべてのデータベースとデータベース内のすべてのオブジェクトを作成します。  
  
-   すべてのデータをインポートします。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの既定の照合順序を変更する代わりに、新しく作成するデータベースごとに既定の照合順序を指定することができます。  
  
## <a name="see-also"></a>参照  
 [Collation and Unicode Support](collation-and-unicode-support.md)   
 [データベースの照合順序の設定または変更](set-or-change-the-database-collation.md)   
 [列の照合順序の設定または変更](set-or-change-the-column-collation.md)   
 [システム データベースの再構築](../databases/system-databases.md)  
  
  