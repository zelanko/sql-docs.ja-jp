---
title: MSSQLSERVER_9524 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 9524 (Database Engine error)
ms.assetid: 12da7931-e124-4466-889c-046f1b7b7bfd
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 527cdb6b0e56b581f670b2119cece017c95e7f69
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver9524"></a>MSSQLSERVER_9524
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|9254|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|XMLERR_INVALID_COLUMNSET_XML|  
|メッセージ テキスト|指定された XML コンテンツが、スパース列セットに必要な XML 形式に準拠していません。|  
  
## <a name="explanation"></a>説明  
列セットを変更しようとしました。 列セットの XML コンテンツは、列セットの形式の制限を満たしている必要があります。 列セットの一般的な形式は次のとおりです。  
  
`<column_name_1>value1</column_name_1><column_name_2>value2</column_name_2>...`  
  
列セットの詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックのトピック「列セットの使用」を参照してください。  
  
## <a name="user-action"></a>ユーザーの操作  
ステートメント内の列セットの XML の形式を修正します。  
  
