---
title: データ移行レポート (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: d63aa7e2-62c6-4c84-b3da-dcf2d89ee134
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 0d58f07f4e9d43f78c9c8990d174030cce484781
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68264250"
---
# <a name="data-migration-report--oracletosql"></a>データ移行レポート (OracleToSQL)
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
  
