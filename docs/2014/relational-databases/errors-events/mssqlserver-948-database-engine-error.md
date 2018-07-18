---
title: MSSQLSERVER_948 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- "948"
helpviewer_keywords:
- 948 (Database Engine error)
ms.assetid: 95c4ad45-a518-4165-a5c4-6e6b932b0570
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 45c987dea690125de2784068b42369a454fafd8d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426381"
---
# <a name="mssqlserver948"></a>MSSQLSERVER_948
    
## <a name="details"></a>詳細  
  
|||  
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
 元のサーバーで実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンを判断します。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、サーバーを右クリックし、をクリックし、**プロパティ**または型`SELECT @@VERSION`クエリ ウィンドウにします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の元のバージョンを使用してデータベースを開きます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで、元のデータベースで有効になっている機能を調べます。 データベースをアタッチする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンで使用できるように、これらの設定を修正します。  
  
  
