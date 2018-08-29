---
title: LocalDB 用 OLE DB Driver for SQL Server のサポート | Microsoft Docs
description: LocalDB 用 OLE DB Driver for SQL Server のサポート
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: d57890c5f0eae3a18d68d904dd34ba20d41cce00
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43020651"
---
# <a name="ole-db-driver-for-sql-server-support-for-localdb"></a>LocalDB 用 OLE DB Driver for SQL Server のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 以降、SQLServer の簡易バージョンである LocalDB を使用できるようになります。 ここでは、LocalDB インスタンス内のデータベースに接続する方法について説明します。  
  
## <a name="remarks"></a>Remarks  
 LocalDB のインストール方法や LocalDB インスタンスの構成方法など、LocalDB の詳細については、以下を参照してください。  
  
-   [SQL Server Express LocalDB リファレンス](../../../relational-databases/sql-server-express-localdb-reference.md)  
  
-   [SQL Server 2016 Express LocalDB](../../../database-engine/configure-windows/sql-server-2016-express-localdb.md)  
  
 要約すると、LocalDB では次の操作を実行できます。  
  
-   使用**sqllocaldb.exe は**を既定のインスタンスの名前を検出します。  
  
-   **AttachDBFilename** 接続文字列キーワードを使用して、サーバーをアタッチするデータベース ファイルを指定できます。 **AttachDBFilename** を使用するときに、**Database** 接続文字列キーワードを使用してデータベース名を指定しなかった場合、データベースはアプリケーションの終了時に LocalDB インスタンスから削除されます。  
  
-   接続文字列では、次のように LocalDB インスタンスを指定します。  
  
```  
SERVER=(localdb)\v11.0  
```  
  
 必要に応じて、sqllocaldb.exe を使用して LocalDB インスタンスを作成できます。 また、sqlcmd.exe を使用して、LocalDB インスタンスのデータベースの追加と変更を実行できます。 たとえば、 **sqlcmd-s (localdb) \v11.0**します。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server の機能](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
