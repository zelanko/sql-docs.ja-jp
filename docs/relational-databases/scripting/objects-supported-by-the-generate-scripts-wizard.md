---
title: "スクリプト生成ウィザードでサポートされるオブジェクト | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
caps.latest.revision: "7"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2b775783cf11a74bbf5ddfd2641f8dc6b483a6ff
ms.sourcegitcommit: b603dcac7326bba387befe68544619e026e6a15e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>スクリプト生成ウィザードでサポートされるオブジェクト
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] スクリプトの生成とパブリッシュ ウィザードでは、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] でサポートされるオブジェクトのサブセットをサポートします。  
  
## <a name="supported-objects"></a>サポート対象のオブジェクト  
 次の表は、スクリプトの生成とパブリッシュ ウィザードでサポートされる、パブリッシュできるオブジェクトの一覧です。  
  
||||||  
|-|-|-|-|-|  
|アプリケーション ロール|データベース ロール|スキーマ|ユーザー定義集計|ビュー*|  
|アセンブリ|DEFAULT 制約|ストアド プロシージャ*|ユーザー定義データ型|XML スキーマ コレクション|  
|CHECK 制約|フルテキスト カタログ|シノニム|ユーザー定義関数||  
|CLR (共通言語ランタイム) ストアド プロシージャ*|インデックス|テーブル|ユーザー定義テーブル||  
|CLR ユーザー定義関数|Rule|ユーザー**|ユーザー定義型||  
  
 * 暗号化されずにパブリッシュされます。  
  
 ** データベースに存在するシステム ユーザー以外のユーザーはすべてロールとしてパブリッシュされます。  
  
  
