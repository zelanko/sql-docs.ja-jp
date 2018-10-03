---
title: 次のフェッチ位置 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 529580a01fc0ca44aaaa68db7524efc80c985140
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47638990"
---
# <a name="fetching-rows---next-fetch-position"></a>行のフェッチ - 次のフェッチ位置
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは常に追跡の次のフェッチ位置のためをへの呼び出しのシーケンス、 **GetNextRows**メソッド (の方向、または介在する変更の呼び出しをスキップ、なし、 **FindNextRow**、**シーク**、または**RestartPosition**メソッド) をスキップまたは任意の行を繰り返しせずに行セット全体を読み取ります。 **IRowset::GetNextRows**、**IRowset::RestartPosition**、または **IRowsetIndex::Seek** を呼び出すか、*pBookmark* 値に NULL を指定して **FindNextRow** を呼び出すことにより、次のフェッチ位置が変更されます。 *pBookmark* 値に NULL 以外の値を指定して **FindNextRow** を呼び出しても、次のフェッチ位置には影響しません。  
  
## <a name="see-also"></a>参照  
 [行のフェッチ](../../relational-databases/native-client-ole-db-rowsets/fetching-rows.md)  
  
  
