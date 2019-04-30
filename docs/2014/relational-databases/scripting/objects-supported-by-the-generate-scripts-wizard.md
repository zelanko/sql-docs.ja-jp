---
title: スクリプト生成ウィザードでサポートされるオブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 32148fabf2e10e620f308bad63648e3e74f48e86
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63143447"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>スクリプト生成ウィザードでサポートされるオブジェクト
  スクリプトの生成とパブリッシュ ウィザードは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]によってサポートされるオブジェクトのサブセットをサポートします。  
  
## <a name="supported-objects"></a>サポート対象のオブジェクト  
 次の表は、スクリプトの生成とパブリッシュ ウィザードでサポートされる、パブリッシュできるオブジェクトの一覧です。  
  
||||||  
|-|-|-|-|-|  
|アプリケーション ロール|データベース ロール|スキーマ|ユーザー定義集計|ビュー<sup>1</sup>|  
|アセンブリ|DEFAULT 制約|ストアド プロシージャ<sup>1</sup>|ユーザー定義データ型|XML スキーマ コレクション|  
|CHECK 制約|フルテキスト カタログ|シノニム|ユーザー定義関数||  
|CLR (共通言語ランタイム) ストアド プロシージャ<sup>1</sup>|インデックス|テーブル|ユーザー定義テーブル||  
|CLR ユーザー定義関数|Rule|ユーザー<sup>2</sup>|ユーザー定義型||  
  
 <sup>1</sup>暗号化されずにパブリッシュします。  
  
 <sup>2</sup>データベース内に存在するすべてのシステム以外のユーザーがロールとしてパブリッシュされます。  
  
  
