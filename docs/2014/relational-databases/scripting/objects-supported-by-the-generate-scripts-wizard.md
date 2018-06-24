---
title: スクリプト生成ウィザードでサポートされるオブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
caps.latest.revision: 5
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f102fa4366106581c5f3ec4ff141d537531dbaa4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072966"
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
  
 <sup>2</sup>データベース内に存在する非システムのすべてのユーザーがロールとしてパブリッシュされます。  
  
  