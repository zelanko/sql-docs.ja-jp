---
title: 戻りで行セットを作成します。マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
- Execute method
ms.assetid: 9b530b7d-8165-49d4-a978-5ced17c6705e
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 227211d860e250d9cb179940b1d671a18cddc219
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68126897"
---
# <a name="creating-rowsets-with-icommandexecute"></a>ICommand::Execute を使用した行セットの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **ICommand::Execute** メソッドを使用して作成された行セットの場合、結果の行セットに設定するプロパティで、コマンドのテキストを制約できます。 これは、動的コマンド テキストをサポートするコンシューマーにとって特に重要です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダーが使用することはできません[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]多くのコマンドで生成された複数の行セットの結果をサポートするカーソルです。 コンシューマーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] カーソル サポートを必要とする行セットを要求した場合に、コマンド テキストが結果として複数行を生成すると、エラーが発生します。 詳細についてを参照してください[コマンドは結果を複数の行セットを生成する](../../relational-databases/native-client-ole-db-commands/commands-generating-multiple-rowset-results.md)です。  
  
 スクロール可能な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でネイティブ クライアント OLE DB プロバイダーの行セットがサポートされている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のカーソルです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、他のデータベース ユーザーの変更によって影響を受けるカーソルに制限が設けらます。 たとえば、一部のカーソル内の行は順序付けできません。この場合に、SQL ORDER BY 句を含むコマンドを使用して行セットを作成しようとすると、エラーが発生します。 詳細については、「[行セットと SQL Server カーソル](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [行セット](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
