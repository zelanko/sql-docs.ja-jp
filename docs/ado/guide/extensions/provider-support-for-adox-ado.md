---
title: ADOX のプロバイダーサポート (ADO) |Microsoft Docs
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
ms.openlocfilehash: 2b07f4563d54254310c08c8c132d0729b8ccdc6b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67923214"
---
# <a name="provider-support-for-adox-ado"></a>ADOX のプロバイダーのサポート (ADO)
OLE DB データプロバイダーによっては、ADOX の特定の機能がサポートされていません。 ADOX は、 [OLE DB Provider For Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)で完全にサポートされています。 次の表に、 [microsoft OLE DB provider for SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md)、 [microsoft OLE DB provider for ODBC](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-odbc.md)、または[Microsoft OLE DB Provider for Oracle](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-oracle.md)でサポートされていない機能を示します。 ADOX は、他の Microsoft OLE DB プロバイダーではサポートされていません。  
  
## <a name="microsoft-ole-db-provider-for-sql-server"></a>Microsoft OLE DB Provider for SQL Server  
  
|オブジェクトまたはコレクション|使用制限|  
|--------------------------|-----------------------|  
|**Tables**コレクション|プロパティは、オブジェクトの作成前には読み取り/書き込みが行われ、既存のオブジェクトを参照する場合は読み取り専用になります。|  
|**Views**コレクション|**ビュー**はサポートされていません。|  
|**Procedures**コレクション|**Append**メソッドと**Delete**メソッドはサポートされていません。|  
|**プロシージャ**オブジェクト|**Command**プロパティはサポートされていません。|  
|**Keys**コレクション|**Append**メソッドと**Delete**メソッドはサポートされていません。|  
|**Users**コレクション|**ユーザー**はサポートされていません。|  
|**Groups**コレクション|**グループ**はサポートされていません。|  
  
## <a name="microsoft-ole-db-provider-for-odbc"></a>Microsoft OLE DB Provider for ODBC  
  
|オブジェクトまたはコレクション|使用制限|  
|--------------------------|-----------------------|  
|**Catalog**オブジェクト|**Create**メソッドはサポートされていません。|  
|**Tables**コレクション|**Append**メソッドと**Delete**メソッドはサポートされていません。 プロパティは、オブジェクトの作成前には読み取り/書き込みが行われ、既存のオブジェクトを参照する場合は読み取り専用になります。|  
|**Procedures**コレクション|**Append**メソッドと**Delete**メソッドはサポートされていません。|  
|**プロシージャ**オブジェクト|**Command**プロパティはサポートされていません。|  
|**Indexes**コレクション|**Append**メソッドと**Delete**メソッドはサポートされていません。|  
|**Keys**コレクション|**Append**メソッドと**Delete**メソッドはサポートされていません。|  
|**Users**コレクション|**ユーザー**はサポートされていません。|  
|**Groups**コレクション|**グループ**はサポートされていません。|  
  
## <a name="microsoft-ole-db-provider-for-oracle"></a>Microsoft OLE DB Provider for Oracle  
  
|オブジェクトまたはコレクション|使用制限|  
|--------------------------|-----------------------|  
|**Catalog**オブジェクト|**Create**メソッドはサポートされていません。|  
|**Tables**コレクション|**Append**メソッドと**Delete**メソッドはサポートされていません。 プロパティは、オブジェクトの作成前には読み取り/書き込みが行われ、既存のオブジェクトを参照する場合は読み取り専用になります。|  
|**Views**コレクション|**Append**メソッドと**Delete**メソッドはサポートされていません。|  
|オブジェクトの**表示**|**Command**プロパティはサポートされていません。|  
|**Procedures**オブジェクト|**Append**メソッドと**Delete**メソッドはサポートされていません。|  
|**プロシージャ**オブジェクト|**Command**プロパティはサポートされていません。|  
|**Indexes**コレクション|**Append**メソッドと**Delete**メソッドはサポートされていません。|  
|**Keys**コレクション|**Append**メソッドと**Delete**メソッドはサポートされていません。|  
|**Users**コレクション|**ユーザー**はサポートされていません。|  
|**Groups**コレクション|**グループ**はサポートされていません。|
