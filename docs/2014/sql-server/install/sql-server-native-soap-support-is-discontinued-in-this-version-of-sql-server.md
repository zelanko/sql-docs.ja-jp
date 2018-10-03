---
title: SQL Server のネイティブ SOAP サポートは、このバージョンの SQL Server では継続されません。 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 80fd692b-1cea-4139-8e80-454d3e81c76d
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c9c3af432ac614a11bb6321af87e28f9675f806a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48183812"
---
# <a name="sql-server-native-soap-support-is-discontinued-in-this-version-of-sql-server"></a>SQL Server のネイティブ SOAP サポートは、このバージョンの SQL Server では継続されません。
  アップグレード アドバイザーによって、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネイティブ XML Web サービスの使用が検出されました。  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>説明  
 この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リリースでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ネイティブ XML Web サービスが削除されています。  
  
## <a name="discovering-where-you-use-native-xml-web-services"></a>ネイティブ XML Web サービスの使用箇所の確認  
 アプリケーションでネイティブ XML Web サービスが使用されるのは、次に示すような箇所です。  
  
-   アップグレード アドバイザーを実行するとき  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンをアップグレードするとき  
  
## <a name="corrective-action"></a>修正措置  
 ネイティブ XML Web サービスを現在使用しているアプリケーションは変更してください。  
  
  
