---
title: SQL Server のプロパティ ([FILESTREAM] ページ) | Microsoft Docs
description: SQL Server の FILESTREAM 設定について説明します。 FILESTREAM を有効にする方法、およびリモート クライアント アクセスやその他のプロパティを構成する方法について説明します。
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.serverproperties.filestream.f1
helpviewer_keywords:
- FILESTREAM [SQL Server], properties page
ms.assetid: 8a8d38d3-e97a-4b09-a40b-659b2e3a5c47
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 81edbd9bfc913f9d339625a993f866d44e1a313b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730935"
---
# <a name="server-properties---filestream-page"></a>Server のプロパティ - [FILESTREAM] ページ
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  このページを使用すると、このインストールの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] に対して FILESTREAM を有効にすることができます。  
  
## <a name="ui-element-list"></a>UI 要素の一覧  
 **[Transact-SQL アクセスに対して FILESTREAM を有効にする]**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスに対して FILESTREAM を有効にする場合にオンにします。 他のコントロール オプションを使用できるようにするには、先にこのコントロールをオンにする必要があります。  
  
 **[ファイル I/O ストリーム アクセスに対して FILESTREAM を有効にする]**  
 FILESTREAM の Win32 ストリーム アクセスを有効にする場合にオンにします。  
  
 **[Windows 共有名]**  
 このコントロールは、FILESTREAM データを格納する Windows 共有の名前を入力する場合に使用します。  
  
 **[リモート クライアントに FILESTREAM データへのストリーム アクセスを許可する]**  
 このコントロールは、リモート クライアントにこのサーバー上のこの FILESTREAM データへのアクセスを許可する場合にオンにします。  
  
## <a name="see-also"></a>参照  
 [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
