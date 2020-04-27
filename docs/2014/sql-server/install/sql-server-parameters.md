---
title: SQL Server Parameters |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine analysis [Upgrade Advisor]
- SQL Server Upgrade Advisor, Database Engine
- Upgrade Advisor [SQL Server], Database Engine
- analyzing system [Upgrade Advisor], Database Engine
ms.assetid: 44a18bfe-e593-47a5-995f-382c01d3f618
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e528b94e51238a06a9776e58693c3093f4bfb831
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66091875"
---
# <a name="sql-server-parameters"></a>SQL Server パラメーター
  このページでは、[!INCLUDE[ssDE](../../includes/ssde-md.md)]の分析で使用するパラメーターを設定します。 1 つ、複数、またはすべてのデータベースの分析、[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用して作成されたトレース ファイルの分析、および SQL バッチ ファイルの分析を行うことができます。  
  
> [!NOTE]  
>  分析対象のトレース ファイルまたは SQL バッチ ファイルを送信する場合に限り、一部のアップグレード問題が検出される可能性があります。  
  
## <a name="options"></a>オプション  
 **[分析するデータベース]**  
 すべてのデータベースを分析するには、[**すべてのデータベース**] チェックボックスをオンにします。 データベースを選択して分析するには、各データベースの横にあるチェック ボックスをオンにしてスキャンの対象とします。  
  
 **[トレース ファイルの分析]**  
 ファイル システムのトレース ファイルを分析するには、このチェック ボックスをオンにします。  
  
 **[トレース ファイルのパス]**  
 1 つ以上のファイルを分析できます。 場所を参照して複数のファイルを選択したり、複数のファイル名を指定できます。 各ファイルへの完全パス名およびファイル名を使用し、パイプ文字 (|) でエントリを区切ります。  
  
 [**トレースファイルの分析**] を有効にすると、パス名とファイル名を入力するまで [**次へ**] が無効になります。  
  
 **バッチ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ファイルの分析**  
 ファイル システムの [!INCLUDE[tsql](../../includes/tsql-md.md)] バッチ ファイルを分析するには、このチェック ボックスをオンにします。  
  
 **バッチファイル[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のパス**  
 1 つ以上のバッチ ファイルを分析できます。 場所を参照して複数のファイルを選択したり、複数のファイル名を入力できます。 各ファイルへの完全パス名およびファイル名を使用し、パイプ文字 (|) でエントリを区切ります。  
  
 [ **SQL バッチファイルの分析**] を有効にすると、パス名とファイル名を入力するまで **[次へ**] ボタンが無効になります。  
  
 **[SQL バッチ区切り記号]**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの個別のバッチに使用するテキストです。 既定値は **[** 実行] です。  
  
## <a name="see-also"></a>参照  
 [アップグレードアドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [アップグレード アドバイザーのユーザー インターフェイス リファレンス](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
