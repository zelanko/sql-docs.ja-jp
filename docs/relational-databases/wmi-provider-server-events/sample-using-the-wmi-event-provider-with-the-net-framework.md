---
title: 'サンプル: .NET での WMI イベントプロバイダーの使用'
description: サンプル C# アプリケーションでは、WMI イベントプロバイダーを使用して、SQL Server のインスタンスで発生するすべてのデータ定義言語イベントのイベントデータを返します。
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Server Events, samples
- sample applications [WMI]
- managed code [WMI]
ms.assetid: 3d7aa7e9-0bb3-4a5b-9a3c-047f3240a6f8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1f0216b39c9291bbce60fb39e4583ddeee2618b7
ms.sourcegitcommit: bf5e9cb3a2caa25d0a37f401b3806b7baa5adea8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/24/2020
ms.locfileid: "85295375"
---
# <a name="sample-using-the-wmi-event-provider-with-the-net-framework"></a>サンプル:.NET Framework での WMI イベント プロバイダーの使用
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  次のサンプルでは、C# でアプリケーションを作成しています。WMI イベント プロバイダーを使用し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの既定のインストールで発生したすべての DDL (データ定義言語) イベントに対応するイベント データを返します。  
  
## <a name="example"></a>例  
 この例は、次のコマンド ファイルを使用してコンパイルします。  
  
```  
set compiler_path=C:\WINNT\Microsoft.NET\Framework\v2.0.50110  
  
%compiler_path%\csc %1  
```  
  
```  
using System;  
using System.Management;  
  
class SQLWEPExample   
{  
    public static void Main(string[] args)  
    {  
        string query =  @"SELECT * FROM DDL_EVENTS " ;  
        // Default namespace for default instance of SQL Server   
        string managementPath =  
            @"\\.\root\Microsoft\SqlServer\ServerEvents\MSSQLSERVER";  
        ManagementEventWatcher  watcher =   
            new ManagementEventWatcher(new WqlEventQuery (query));  
        ManagementScope scope = new ManagementScope (managementPath);  
        scope.Connect();  
        watcher.Scope = scope;  
        Console.WriteLine("Watching...");  
        while (true)  
        {  
            ManagementBaseObject obj = watcher.WaitForNextEvent();  
            Console.WriteLine("Event!");  
            foreach (PropertyData data in obj.Properties)  
            {  
                Console.Write("{0}:", data.Name);  
                if (data.Value == null)  
                {  
                    Console.WriteLine("<null>");  
                }  
                else  
                {  
                    Console.WriteLine(data.Value.ToString());  
                }  
            }  
            Console.WriteLine("-----");  
            Console.WriteLine();  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [WMI Provider for Server Events の概念](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)  
  
  
