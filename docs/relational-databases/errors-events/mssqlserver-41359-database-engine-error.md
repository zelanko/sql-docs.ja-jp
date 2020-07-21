---
title: MSSQLSERVER_41359 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41359 (Database Engine error)
ms.assetid: 02b717c7-9170-4676-b0f6-4dec9eb5b5d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b5372ffbeed279bf8c2c2f3adc8ad00dd8436fe3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765326"
---
# <a name="mssqlserver_41359"></a>MSSQLSERVER_41359
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|41359|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED|  
|メッセージ テキスト|メモリ最適化テーブルにアクセスするクエリで分離レベルに READ COMMITTED が使用されており、データベース オプション READ_COMMITTED_SNAPSHOT が ON に設定されている場合には、ディスク ベース テーブルにアクセスできません。 メモリ最適化テーブルには WITH (SNAPSHOT) などのテーブル ヒントを使用して、サポートされる分離レベルを指定します。|  
  
## <a name="explanation"></a>説明  
READ_COMMITTED_SNAPSHOT が ON のデータベースでは、メモリ最適化テーブルとディスク ベース テーブルのどちらにもアクセスするトランザクションがサポートされません。  
  
## <a name="user-action"></a>ユーザーの操作  
READ_COMMITTED_SNAPSHOT を OFF に設定するか、WITH (SNAPSHOT) などのテーブル レベルのヒントを使用してメモリ最適化テーブルでサポートされる分離レベルを指定してください。 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[インメモリ OLTP &#40;インメモリ最適化&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
