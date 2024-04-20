const express = require('express');

const app = express();

app.get('/', (req, res) => {
  res.send('Hello Express app!')
});

app.listen(3000, () => {
console.log("Made By MBF Team")
});


const Discord = require('discord.js');
const client = new Discord.Client({
  intents: ["GUILDS", "GUILD_MEMBERS", "GUILD_MESSAGES"]
})
const prefix = '-'
const channel = '1132448657216634921'

client.on("ready", () => {
  console.log(`${client.user.tag} Working...`)
})
var approx = require('approximate-number');

client.on("messageCreate", (message) => {
  if(message.author.bot) return;
  if (message.channel.id == `${channel}`) { 
  let args = message.content
    
if (args.endsWith("m") || args.endsWith("M")) args = args.replace(/m/gi, "") * 1000000;
else if (args.endsWith("k") || args.endsWith("K")) args = args.replace(/k/gi, "") * 1000;
else if (args.endsWith("B") || args.endsWith("b")) args = args.replace(/b/gi, "") * 1000000000; 

    let args2 = parseInt(args) 

    let tax = Math.floor(args2 * (20) / (19) + (1))
    let tax2 = Math.floor(args2 * (20) / (19) + (1)-(args2))
    let tax3 = Math.floor(tax2 * (20) / (19) + (1))
    let tax4 = Math.floor(tax2 + tax3 + args2)

    let errorembed3 = new Discord.MessageEmbed()
    .setTitle(`**Error**`)
    .setDescription(`> **يجب عليك ان تكتب رقم بعد الأمر** ❌`)
    .setThumbnail(`${message.guild.iconURL({ dynamic: true })}`)
    .setTimestamp()
    if (!args2) return message.channel.send({embeds: [errorembed3]});
    let errorembed = new Discord.MessageEmbed()
    .setTitle(`Error`)
    .setDescription(`> **يجب علي ادخل مبلغ اكثر من 1** ❌`)
    .setThumbnail(`${message.guild.iconURL({ dynamic: true })}`)
    .setTimestamp()
    if (args2 < 1 ) return message.channel.send({embeds: [errorembed]});
    let embed3 = new Discord.MessageEmbed()
    .setTitle(`ضريبه بروبوت : ${args2}`)  
    .setDescription(`Tax : 1`)
    .setThumbnail(`${message.guild.iconURL({ dynamic: true })}`)
    .setTimestamp()
    if (args2 == 1) return message.channel.send({embeds: [embed3]});
    let embed = new Discord.MessageEmbed()
        .setTitle(`[${approx(args2)}] ضريبه بروبوت : ${args2} `)
    .setDescription(`> **[${approx(tax2)}] ضريبه : ${tax2}  **\n\n> **[${approx(tax3)}] وسيط : ${tax3}  **\n\n> **[${approx(tax)}] المبلغ + الضريبه : ${tax} ** \n\n> **[${approx(tax4)}] المبلغ + الضريبه + الوسيط : ${tax4}  **`)
    .setThumbnail(`${message.guild.iconURL({ dynamic: true })}`)
    .setTimestamp()
    message.channel.send({embeds: [embed]});
  }

})





/////autokill

client.login(process.env.token).catch(() => console.log("Invalid Token Was Provided.\nPlease put the TOKEN in secret"));
const { AutoKill } = require('autokill')
AutoKill({Client: client, Time: 5000})

process.on("unhandledRejection", error => {
  console.log(error)
});
