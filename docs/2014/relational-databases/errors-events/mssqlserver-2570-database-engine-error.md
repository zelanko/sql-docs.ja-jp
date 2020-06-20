---
title: MSSQLSERVER_2570 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2570 (Database Engine error)
ms.assetid: 29800aa9-81aa-4371-992c-487dbb617f46
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 79137d0f70c05c6aa7b758f7e073d152681a14b4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054069"
---
# <a name="mssqlserver_2570"></a>MSSQLSERVER_2570
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2570|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_COLUMN_VALUE_OUT_OF_RANGE|  
|メッセージ テキスト|ページ P_ID、オブジェクト ID O_ID のスロット S_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE)。 列 COLUMN_NAME の値が、データ型 "DATATYPE" の範囲外です。 列を有効な値に更新してください。|  
  
## <a name="explanation"></a>説明  
 指定した列に格納されている値は、列のデータ型に対する有効値の範囲外です。  
  
## <a name="user-action"></a>ユーザーの操作  
 このエラーは修復できません。 列のデータ型に対する範囲内に収まるよう列の値を更新して、再度コマンドを実行してください。  詳細については、サポート技術情報の資料 [923247](https://support.microsoft.com/kb/923247) を参照してください。  
  
## <a name="see-also"></a>参照  
 [UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql)   
 [データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
