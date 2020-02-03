---
title: スクリプト生成ウィザードでサポートされるオブジェクト
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c14ea09d45c59def95f078eb87e72e2a70925892
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75253764"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a>スクリプト生成ウィザードでサポートされるオブジェクト
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  スクリプトの生成とパブリッシュ ウィザードは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]によってサポートされるオブジェクトのサブセットをサポートします。  
  
## <a name="supported-objects"></a>サポート対象のオブジェクト  
 次の表は、スクリプトの生成とパブリッシュ ウィザードでサポートされる、パブリッシュできるオブジェクトの一覧です。  
  
||||||  
|-|-|-|-|-|  
|アプリケーション ロール|データベース ロール|スキーマ|ユーザー定義集計|ビュー*|  
|アセンブリ|DEFAULT 制約|ストアド プロシージャ*|ユーザー定義データ型|XML スキーマ コレクション|  
|CHECK 制約|フルテキスト カタログ|シノニム|ユーザー定義関数||  
|CLR (共通言語ランタイム) ストアド プロシージャ*|インデックス|テーブル|ユーザー定義テーブル||  
|CLR ユーザー定義関数|ルール|ユーザー**|ユーザー定義型||  
  
 \* 暗号化されずにパブリッシュされます。  
  
 ** データベースに存在するシステム ユーザー以外のユーザーはすべてロールとしてパブリッシュされます。  
  
  
