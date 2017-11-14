---
title: "ADOX (ADO) をサポートするプロバイダー |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ADOX provider support [ADO]
ms.assetid: 64234ce5-dc46-4c8a-a316-61956b6b9abb
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b15df02c70e2dcdc2efb2ba468b76219a233d65a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="provider-support-for-adox-ado"></a>ADOX (ADO) をサポートするプロバイダー
ADOX の特定の機能は、OLE DB データ プロバイダーによってサポートされているがします。 ADOX が完全にサポート、 [OLE DB Provider for Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)です。 サポートされていない機能、 [Microsoft OLE DB Provider for SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)、 [Microsoft OLE DB Provider for ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)、または[Microsoft OLE DB Provider for Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md)は次の表に一覧表示されます。 ADOX は、その他のすべての Microsoft OLE DB プロバイダーによってサポートされていません。  
  
## <a name="microsoft-ole-db-provider-for-sql-server"></a>Microsoft OLE DB Provider for SQL Server  
  
|オブジェクトまたはコレクション|使用制限|  
|--------------------------|-----------------------|  
|**テーブル**コレクション|プロパティは、既存のオブジェクトを参照するときに、読み取り/書き込み、オブジェクトを作成する前に、および読み取り専用がします。|  
|**ビュー**コレクション|**ビュー**はサポートされていません。|  
|**プロシージャ**コレクション|**Append**と**削除**メソッドはサポートされていません。|  
|**プロシージャ**オブジェクト|**コマンド**プロパティがサポートされていません。|  
|**キー**コレクション|**Append**と**削除**メソッドはサポートされていません。|  
|**ユーザー**コレクション|**ユーザー**はサポートされていません。|  
|**グループ**コレクション|**グループ**はサポートされていません。|  
  
## <a name="microsoft-ole-db-provider-for-odbc"></a>Microsoft OLE DB Provider for ODBC  
  
|オブジェクトまたはコレクション|使用制限|  
|--------------------------|-----------------------|  
|**カタログ**オブジェクト|**作成**メソッドがサポートされていません。|  
|**テーブル**コレクション|**Append**と**削除**メソッドはサポートされていません。 プロパティは、既存のオブジェクトを参照するときに、読み取り/書き込み、オブジェクトを作成する前に、および読み取り専用がします。|  
|**プロシージャ**コレクション|**Append**と**削除**メソッドはサポートされていません。|  
|**プロシージャ**オブジェクト|**コマンド**プロパティがサポートされていません。|  
|**インデックス**コレクション|**Append**と**削除**メソッドはサポートされていません。|  
|**キー**コレクション|**Append**と**削除**メソッドはサポートされていません。|  
|**ユーザー**コレクション|**ユーザー**はサポートされていません。|  
|**グループ**コレクション|**グループ**はサポートされていません。|  
  
## <a name="microsoft-ole-db-provider-for-oracle"></a>Microsoft OLE DB Provider for Oracle  
  
|オブジェクトまたはコレクション|使用制限|  
|--------------------------|-----------------------|  
|**カタログ**オブジェクト|**作成**メソッドがサポートされていません。|  
|**テーブル**コレクション|**Append**と**削除**メソッドはサポートされていません。 プロパティは、既存のオブジェクトを参照するときに、読み取り/書き込み、オブジェクトを作成する前に、および読み取り専用がします。|  
|**ビュー**コレクション|**Append**と**削除**メソッドはサポートされていません。|  
|**ビュー**オブジェクト|**コマンド**プロパティがサポートされていません。|  
|**プロシージャ**オブジェクト|**Append**と**削除**メソッドはサポートされていません。|  
|**プロシージャ**オブジェクト|**コマンド**プロパティがサポートされていません。|  
|**インデックス**コレクション|**Append**と**削除**メソッドはサポートされていません。|  
|**キー**コレクション|**Append**と**削除**メソッドはサポートされていません。|  
|**ユーザー**コレクション|**ユーザー**はサポートされていません。|  
|**グループ**コレクション|**グループ**はサポートされていません。|

