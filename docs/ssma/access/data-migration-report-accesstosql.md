---
title: データ移行レポート (データ移動 Sql) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: b090b327-cec6-4d9a-a670-8f96e8ff0046
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 4d552114800b2d5d0148e3681f1fd165a914f654
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68006587"
---
# <a name="data-migration-report-accesstosql"></a>データ移行レポート (データ移動 Sql)
[**データ移行レポート**] ダイアログボックスは、にデータを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行した後に表示されます。  
  
## <a name="options"></a>オプション  
**状態**  
転送元データベースから転送先データベースへのデータ移行の状態が表示されます。  
  
**From**  
ソーステーブルです。  
  
**To**  
対象のテーブル。  
  
**行の合計数**  
ソーステーブル内のデータ行の数。  
  
**正常に移行された行の数**  
ターゲットテーブルに正常に移行されたデータの行の数。  
  
**比率**  
正常に移行された行の割合。  
  
**詳細**  
データの移行に失敗した場合は、クリックすると、レポート内の選択した行の移行の詳細が表示されます。 SSMA には、エラーの理由が表示されます。  
  
**[レポートの保存]**  
レポートをに保存します。CSV (コンマ区切り値) ファイル。 Microsoft Excel を使用して調べることができます。  
  
