---
title: 互換性のないデータベース エンジンのサーバー照合順序 (アップグレード アドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 80f499d6-2c90-49eb-a5b3-0bb5b7faaa3b
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e182df78fc7faae8a50092fd51a8f2c0964fe2bc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37286648"
---
# <a name="incompatible-database-engine-server-collation-upgrade-advisor"></a>互換性のないデータベース エンジン サーバーの照合順序 (アップグレード アドバイザー)
  アップグレード アドバイザーが検出された[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のインスタンスを使用して、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]互換性のないサーバーの照合順序を使用して構成されています。  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード。|  
  
## <a name="component"></a>コンポーネント  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>説明  
 アップグレード アドバイザーが検出された[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のインスタンスを使用して、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]互換性のないサーバーの照合順序を使用して構成されています。  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードでは、SharePoint 共有サービス アーキテクチャで使用します。 SharePoint では、大文字と小文字の区別、サーバー照合順序、またはバイナリ サーバー照合順序用に構成された [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] はサポートされません。 互換性のない照合順序には、既定で大文字と小文字を区別するかバイナリである照合順序と、既定では互換性があるものの、次の照合順序指定子のいずれかで構成されている基本照合順序が含まれます。  
  
-   **Binary**  
  
-   **大文字**  
  
-   **バイナリ コード ポイント**  
  
 現在の [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] サーバー照合順序は互換性がないため、アップグレードがブロックされます。  
  
## <a name="corrective-action"></a>修正措置  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] サーバーの照合順序プロパティは変更できません。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のアップグレードを完了できなくなります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールを、互換性のあるサーバー照合順序を使用している新しいサーバーに移行する必要があります。 詳細については、以下を参照してください。  
  
-   [Reporting Services のアップグレードと移行](http://go.microsoft.com/fwlink/?LinkId=233227)  
  
-   [SQL Server 照合順序の選択](http://go.microsoft.com/fwlink/?LinkId=233226)  
  
  
