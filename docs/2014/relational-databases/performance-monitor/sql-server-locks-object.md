---
title: SQL Server:Locks オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Locks object
- SQLServer:Locks
ms.assetid: ace04f0d-3993-4444-8317-ca39d7087e49
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: cd7773177f6ec9d02df9d3d669abf561919ffe0b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63250608"
---
# <a name="sql-server-locks-object"></a>SQL Server:Locks オブジェクト
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の**SQLServer: locks**オブジェクトには、個々[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のリソースの種類のロックに関する情報が記載されています。 ロックは、複数のトランザクションで同じ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソースが同時に使用されるのを防ぐために、トランザクション中に読み取られたり変更されたりする行などにかけられます。 たとえば、あるトランザクションによってテーブルの行に排他 (X) ロックがかけられると、他のトランザクションはロックが解除されるまでその行を変更できません。 ロックを最小限にとどめるとコンカレンシーが向上し、パフォーマンスが向上します。 異なる種類のリソースのロックを表す複数の **Locks** オブジェクトのインスタンスを同時に監視することができます。  
  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Locks** カウンターについて説明します。  
  
|SQL Server:Locks カウンター|[説明]|  
|-------------------------------|-----------------|  
|**平均待機時間 (ミリ秒)**|待つ必要がある各ロック要求の平均待ち時間 (ミリ秒)。|  
|**ロック要求数/秒**|ロック マネージャーから 1 秒あたりに要求された新しいロックと、ロック変換の数。|  
|**ロックタイムアウト (タイムアウト > 0)/秒**|NOWAIT ロックの要求を除く、1 秒あたりにタイムアウトしたロック要求の数。|  
|**ロックタイムアウト/秒**|NOWAIT ロックの要求を含めた、1 秒あたりにタイムアウトしたロック要求の数。|  
|**ロック待機時間 (ミリ秒)**|最後の 1 秒間のロックの総待機時間 (ミリ秒)。|  
|**ロック待機数/秒**|呼び出し元が待つ必要のあった 1 秒あたりのロック要求の数。|  
|**デッドロック数/秒**|デッドロックが発生した 1 秒あたりのロック要求の数。|  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、以下のリソースをロックできます。  
  
|アイテム|[説明]|  
|----------|-----------------|  
|**_Total**|すべてのロックに関する情報。|  
|**AllocUnit**|アロケーション ユニットのロック。|  
|**Application**|アプリケーションで指定されているリソースのロック。|  
|**[データベース]**|データベース内のすべてのオブジェクトを含むデータベースのロック。|  
|**エクステント**|連続した 8 ページのグループのロック。|  
|**拡張子**|データベース ファイルのロック。|  
|**ヒープ/BTree**|ヒープまたは BTree (HOBT)。 データ ページのヒープまたはインデックスの BTree 構造のロック。|  
|**[キー]**|インデックスの行のロック。|  
|**Metadata**|カタログ情報 (メタデータ) のロック。|  
|**Object**|すべてのデータとインデックスを含む、テーブル、ストアド プロシージャ、ビューなどのロック。 このオブジェクトには、 **sys.all_objects**内のエントリを持つ任意のアイテムが含まれます。|  
|**ページ**|データベース内の 8 KB のページのロック。|  
|**RID**|行 ID。 ヒープ内の単一行のロック。|  
  
## <a name="see-also"></a>参照  
 [リソース使用状況の監視 &#40;システムモニタ&#41;](monitor-resource-usage-system-monitor.md)  
  
  
