---
title: ADOX (ADO) プロバイダーのサポート |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADOX provider support [ADO]
ms.assetid: 64234ce5-dc46-4c8a-a316-61956b6b9abb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6f346779d3a4c8cb43e2b30347ebf6b198d9015
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63126871"
---
# <a name="provider-support-for-adox-ado"></a>ADOX のプロバイダーのサポート (ADO)
ADOX の特定の機能は、OLE DB データ プロバイダーによってサポートされているがします。 ADOX がで完全にサポート、 [OLE DB Provider for Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)します。 サポートされていない機能、 [Microsoft OLE DB Provider for SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)、 [Microsoft OLE DB Provider for ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)、または[Microsoft OLE DB Provider for Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md)は次の表に一覧表示されます。 ADOX は他の Microsoft OLE DB プロバイダーでサポートされていません。  
  
## <a name="microsoft-ole-db-provider-for-sql-server"></a>Microsoft OLE DB Provider for SQL Server  
  
|オブジェクトまたはコレクション|使用制限|  
|--------------------------|-----------------------|  
|**テーブル**コレクション|プロパティは、既存のオブジェクトを参照するときに、オブジェクトの作成前に、読み取り専用読み取り/書き込みです。|  
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
|**テーブル**コレクション|**Append**と**削除**メソッドはサポートされていません。 プロパティは、既存のオブジェクトを参照するときに、オブジェクトの作成前に、読み取り専用読み取り/書き込みです。|  
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
|**テーブル**コレクション|**Append**と**削除**メソッドはサポートされていません。 プロパティは、既存のオブジェクトを参照するときに、オブジェクトの作成前に、読み取り専用読み取り/書き込みです。|  
|**ビュー**コレクション|**Append**と**削除**メソッドはサポートされていません。|  
|**ビュー**オブジェクト|**コマンド**プロパティがサポートされていません。|  
|**プロシージャ**オブジェクト|**Append**と**削除**メソッドはサポートされていません。|  
|**プロシージャ**オブジェクト|**コマンド**プロパティがサポートされていません。|  
|**インデックス**コレクション|**Append**と**削除**メソッドはサポートされていません。|  
|**キー**コレクション|**Append**と**削除**メソッドはサポートされていません。|  
|**ユーザー**コレクション|**ユーザー**はサポートされていません。|  
|**グループ**コレクション|**グループ**はサポートされていません。|
