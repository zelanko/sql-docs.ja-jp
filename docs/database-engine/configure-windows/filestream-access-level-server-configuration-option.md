---
title: "filestream access level サーバー構成オプション | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FILESTREAM [SQL Server], access level
- filestream access level
ms.assetid: b88f6ff2-795e-4730-bfb8-dbc6a958f2ad
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 625dcd6009f4cfe37ac1e4e0d1d2db26ea9e1e66
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="filestream-access-level-server-configuration-option"></a>filestream access level サーバー構成オプション
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに対する FILESTREAM のアクセス レベルを変更するには、filestream_access_level オプションを使用します。  
  
> [!NOTE]  
>  このオプションを有効にする前に、FILESTREAM の Windows 管理者設定を有効にする必要があります。 これらの設定は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール時に有効にできます。また、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して有効にすることもできます。  
  
|値|定義|  
|-----------|----------------|  
|0|このインスタンスに対する FILESTREAM サポートを無効にします。|  
|1|[!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスに対して FILESTREAM を有効にします。|  
|2|[!INCLUDE[tsql](../../includes/tsql-md.md)] アクセスおよび Win32 ストリーム アクセスに対して FILESTREAM を有効にします。|  
  
## <a name="see-also"></a>参照  
 [データベース エンジンの構成 - Filestream](http://msdn.microsoft.com/library/641a10a1-ae52-4d26-8f1c-a032a4aeff02)   
 [FILESTREAM の有効化と構成](../../relational-databases/blob/enable-and-configure-filestream.md)  
  
  

