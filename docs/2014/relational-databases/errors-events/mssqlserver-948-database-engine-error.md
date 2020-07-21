---
title: MSSQLSERVER_948 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "948"
helpviewer_keywords:
- 948 (Database Engine error)
ms.assetid: 95c4ad45-a518-4165-a5c4-6e6b932b0570
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3a554f8cdd312f08e8e0930c0d3eb49776cbc4e8
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553104"
---
# <a name="mssqlserver_948"></a>MSSQLSERVER_948
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|948|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|NA|  
|メッセージ テキスト|データベース '%.*ls' のバージョンは %d なので、開けません。 このサーバーではバージョン %d 以前がサポートされます。 このダウングレード パスはサポートされません。|  
  
## <a name="explanation"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の一部の機能は、データベース ファイルの構造に影響を与えます。 データベースを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスにアタッチする場合、[!INCLUDE[ssDE](../../includes/ssde-md.md)]のバージョンが違っていると、ファイル形式の互換性がない場合があります。  
  
 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Pack 2 以降のバージョンで vardecimal ストレージ形式を使用して、それよりも前のバージョンの [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] でデータベース ファイルをアタッチしようとすると、このエラーが発生することがあります。  
  
## <a name="user-action"></a>ユーザーの操作  
 元のサーバーで実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンを判断します。 で、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] サーバーを右クリックし、[**プロパティ**] をクリックするか、クエリウィンドウを入力し `SELECT @@VERSION` ます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の元のバージョンを使用してデータベースを開きます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで、元のデータベースで有効になっている機能を調べます。 データベースをアタッチする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンで使用できるように、これらの設定を修正します。  
  
  
