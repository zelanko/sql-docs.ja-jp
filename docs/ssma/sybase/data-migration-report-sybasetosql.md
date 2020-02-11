---
title: データ移行レポート (SybaseToSQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: bac234ef-bc16-47e6-8a7c-aa6e76d860c5
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: b05ca315401e587a4a200ff6fc78634993260b07
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029403"
---
# <a name="data-migration-report-sybasetosql"></a>データ移行レポート (SybaseToSQL)
[**データ移行レポート**] ダイアログボックスは、にデータを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行した後に表示されます。  
  
## <a name="options"></a>オプション  
**状態**  
転送元データベースから転送先データベースへのデータ移行の状態が表示されます。  
  
**差出人**  
ソーステーブルです。  
  
**宛先**  
対象のテーブル。  
  
**行の合計数**  
ソーステーブル内のデータ行の数。  
  
**正常に移行された行の数**  
ターゲットテーブルに正常に移行されたデータの行の数。  
  
**比率**  
正常に移行された行の割合。  
  
**詳細**  
データの移行に失敗した場合は、クリックすると、レポート内の選択した行の移行の詳細が表示されます。 SSMA には、エラーの理由が表示されます。  
  
**レポートの保存**  
レポートをに保存します。CSV (コンマ区切り値) ファイル。 Microsoft Excel を使用して調べることができます。  
  
