---
title: テーブル値パラメーター (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, table-valued parameters
- table-valued parameters (OLE DB)
ms.assetid: 4298b73d-615b-4d28-9843-03b4d5fc489e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a759ed6729ce066cbbd5b8c38043402195b62b98
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82704579"
---
# <a name="table-valued-parameters-ole-db"></a>テーブル値パラメーター (OLE DB)
  ここでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでのテーブル値パラメーターのサポートについて説明します。 追加の概要情報については、「[テーブル値パラメーター &#40;SQL Server Native Client&#41;](../native-client/features/table-valued-parameters-sql-server-native-client.md)」を参照してください。 サンプルについては、「[テーブル値パラメーターの使用 &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)」を参照してください。  
  
## <a name="remarks"></a>解説  
 現時点では、複数行データを、パラメーター セット (`ICommand::Execute` の DBPARAMS パラメーター) と共にプロシージャのパラメーターとしてサーバーに送信できます。 パラメーター セットを使用する場合、セットの各要素は、個別のリモート プロシージャ コール (RPC) の要求でサーバーに送信する必要があります。 テーブル値パラメーターの機能は似ていますが、サーバーとの統合はより緊密になっています。 これにより、RPC 要求の数が減少し、サーバーでセットベースの操作が可能になります。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、テーブル値パラメーターが OLE DB `Rowset` オブジェクトとしてサポートされます。 どの `Rowset` オブジェクトも、コンシューマー (つまり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを使用するクライアント アプリケーション) によってテーブル値パラメーターのプレースホルダーとして指定されます。 テーブル値パラメーターは、他の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パラメーターの型と同じように扱われます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによって、作成、検索、指定、バインド、およびスキーマのインターフェイスが提供されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [テーブル値パラメーターの行セットの作成](table-valued-parameter-rowset-creation.md)  
  
-   [テーブル値パラメーターの型の検出](../../database-engine/dev-guide/table-valued-parameter-type-discovery.md)  
  
-   [テーブル値パラメーターを含むコマンドの実行](executing-commands-containing-table-valued-parameters.md)  
  
-   [テーブル値パラメーターへのデータの挿入](inserting-data-into-table-valued-parameters.md)  
  
-   [OLE DB テーブル値パラメーター向けに変更されたスキーマ行セット](schema-rowsets-changed-for-ole-db-table-valued-parameters.md)  
  
-   [OLE DB テーブル値パラメーターの型のサポート](ole-db-table-valued-parameter-type-support.md)  
  
-   [OLE DB テーブル値パラメーターの型のサポート (メソッド)](ole-db-table-valued-parameter-type-support-methods.md)  
  
-   [OLE DB テーブル値パラメーターの型のサポート (プロパティ)](ole-db-table-valued-parameter-type-support-properties.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)   
 [テーブル値パラメーターの使用 &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
