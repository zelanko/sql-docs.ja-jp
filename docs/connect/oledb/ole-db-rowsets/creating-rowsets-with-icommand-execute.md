---
title: Icommand::execute で行セットを作成する |Microsoft ドキュメント
description: Icommand::execute で行セットを作成します。
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, creating
- Execute method
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 3069d9a15ca9e988ed241515d19d66bb7b79e9d3
ms.sourcegitcommit: 03ba89937daeab08aa410eb03a52f1e0d212b44f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/16/2018
ms.locfileid: "35689955"
---
# <a name="creating-rowsets-with-icommandexecute"></a>ICommand::Execute を使用した行セットの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  使用して作成された行セットの**icommand::execute**メソッド、結果の行セットに必要なプロパティは、コマンドのテキストを制約できます。 これは、動的コマンド テキストをサポートするコンシューマーにとって特に重要です。  
  
 SQL Server の OLE DB Driver は使用できません[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]多くのコマンドで生成される複数の行セット結果をサポートするカーソル。 コンシューマーが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] カーソル サポートを必要とする行セットを要求した場合に、コマンド テキストが結果として複数行を生成すると、エラーが発生します。 詳細については、次を参照してください。[コマンドを生成する複数の行セット結果](../../oledb/ole-db-commands/commands-generating-multiple-rowset-results.md)です。  
  
 スクロール可能な OLE DB Driver for SQL Server の行セットでサポートされている[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]カーソル。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、他のデータベース ユーザーの変更によって影響を受けるカーソルに制限が設けらます。 たとえば、一部のカーソル内の行は順序付けできません。この場合に、SQL ORDER BY 句を含むコマンドを使用して行セットを作成しようとすると、エラーが発生します。 詳細については、次を参照してください。[行セットと SQL Server カーソル](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md)です。  
  
## <a name="see-also"></a>参照  
 [行セット](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
