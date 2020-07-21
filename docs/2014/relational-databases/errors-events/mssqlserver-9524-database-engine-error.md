---
title: MSSQLSERVER_9524 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9524 (Database Engine error)
ms.assetid: 12da7931-e124-4466-889c-046f1b7b7bfd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c82132c02376176b5e524f42aadcd343cc40d68b
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553087"
---
# <a name="mssqlserver_9524"></a>MSSQLSERVER_9524
    
## <a name="details"></a>詳細  
  
|属性|値|  
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
  
  
