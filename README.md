# bot-6.0
bot discord
import discord
from discord.ext import commands

import os, random

list_terror = ["RESIDENT EVIL",   "SILENT HILL",    "UNTIL DAWN"]

list_rpg = ["DARK SOULS III",  "DARKEST DUNGEON", "DISCO ELYSI"]

list_jrpg = ["PERSONA 5",   "FINAL FANTASY",   "STAR OCEAN"]

intents = discord.Intents.default()
intents.message_content = True

token = ""

bot = commands.Bot(command_prefix="!", intents=intents)

@bot.event
async def on_ready():
    print("el bot")

@bot.command()
async def hola(ctx):
    await ctx.send(f"hola soy {bot.user}")

@bot.command()
async def meme(ctx):
    files = os.listdir("carpeta1")
    meme_random = random.choice(files)
    meme_path = os.path.join("carpeta1",meme_random)
    await ctx.send(file=discord.File(meme_path))

@bot.command()
async def terror(ctx):
    r_terror = random.choice(list_terror)
    await ctx.send(r_terror)


@bot.command()
async def rpg(ctx):
    r_rpg = random.choice(list_rpg)
    await ctx.send(r_rpg)

@bot.command()
async def jrpg(ctx):
    r_jrpg = random.choice(list_jrpg)
    await ctx.send(r_jrpg)

bot.run(token)
