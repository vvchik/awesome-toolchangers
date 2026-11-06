# Contributing

Pull requests and issues are welcome. The fastest way to suggest a design is the [Add a toolchanger](https://github.com/vvchik/awesome-toolchangers/issues/new?template=add-toolchanger.yml) form. The fastest way to report a wrong value is the [Fix a row](https://github.com/vvchik/awesome-toolchangers/issues/new?template=fix-row.yml) form. A project page and one sentence are enough to start. The maintainer fills the rest.

## What belongs in the catalog

To get a row, a design must meet all of these rules:

- It changes tools or hotends automatically. The printer parks the old tool in a dock and picks up the next one. A coupling locates the tool, and a lock holds it. Manual quick-swaps, IDEX, and multi-hotend heads without a dock do not count.
- The author publishes the files for free. Files in a closed chat group, behind a payment, or re-uploaded by someone else do not count. A promise to publish them later does not count.
- The files include CAD (STEP or a native format).
- A BOM and build instructions exist, as files or inside a manual, README, wiki, or build log.
- The license allows other people to build it.
- At least one person other than the author built it.
- It is not a port or a mod of a design that is already listed. Ports to other printers, dock variants, and toolhead adapters go on the page of the original design. A fork that changes the coupling, the lock, or the dock gets its own row.

If the design files and firmware of a commercial changer are public, it is included. An interesting design without files or builds by other people goes to Concepts and prototypes in OTHER.md. Software and calibration tools are not listed.

Not accepted: homepages or shops instead of project pages, dead links, duplicates, and claims such as "best" or "fastest".

## Sections

[README.md](README.md) has these tables:

- Tool changers: each tool has its own extruder, on the tool or on the frame with a Bowden tube. If a tool has its own extruder motor, it is a tool changer, also when the author calls it a hotend changer.
- Hotend changers: the extruder stays on the carriage, and only the hotend changes.
- Concepts and prototypes: see above.
- Legacy designs: no update in two years and no group with 100 or more members, an archived repository, or a design that a newer version replaced.

README.md keeps only the concepts and legacy designs that the maintainer finds important. [OTHER.md](OTHER.md) keeps the other designs for history: more concepts and legacy designs, and the designs that fail a rule, with the reason.

If a design has both modes, it goes where its default build is. A whole printer built around a changer gets a row under the name of the design. Ports, variants, and builds by other people go on the toolchanger page of the original design. The maintainer can add sections and move rows as the catalog grows.

## What to send

These facts make a row. Send what you can find and link the source of each value:

- Name, project page, and author.
- Why it is interesting, in one or two sentences.
- Coupling: how the tool locates on the carriage, for example Maxwell, Kelvin, pins and bushings, or magnets.
- Lock: what holds the tool, for example magnets, a latch, a cam, or a twist lock, and what opens it: a servo, a motor, or a move against the dock.
- Extruder: on the tool, or on the frame with a Bowden tube.
- Change time: seconds from the last move of the old tool to the first move of the new tool, without purge, prime, and heating. Use the author's number, or time it in a video by the author or a builder.
- Tools: the most tools the author shows working.
- Base printers that the author supports.
- Firmware and plugin, for example Klipper with klipper-toolchanger.
- Latest public revision and the link that proves its date.
- Direct links to CAD, STL, BOM, manual, config, and the author's video.
- Builder groups, with the language and the member count.
- The license and the page where you found it.

## Adding a full row

1. Pick the section. Use the rules above.
2. Copy an existing row of that table and replace every cell. Keep the `<a id="slug">` anchor. The slug is lowercase with hyphens and is reused for the toolchanger folder.
3. Latest version: link the release, changelog, CAD commit, or file upload that proves the date.
4. Counts: only the creator's own pages and videos. For a GitHub repository, copy the star badge from an existing row and change the repository path.
5. Write `—` for a value that you cannot find. Do not guess.
6. Sort the row by GitHub stars, highest first. A row with no repository sorts by its highest like count on a model site, then by the likes of the author's video. Rows with no counts go last.

## Adding the toolchanger page and pictures

1. Create `toolchangers/<slug>/README.md` from an existing page. It repeats the row as a field list and lists all pictures.
2. Name pictures `0-<slug>.jpg`, `1-<slug>.jpg`, and so on. `0-` is the main picture shown in the catalog and the gallery. It shows the changer itself: the tools in their docks, or a tool on the carriage. Keep each picture under 800 px on the long side.
3. Credit every picture to its author on the toolchanger page, with a link to where it was published. Pictures keep their authors' rights.

## Fixing a row

Open a [Fix a row](https://github.com/vvchik/awesome-toolchangers/issues/new?template=fix-row.yml) issue with the correct value and a source link, or send a pull request that changes only that cell.

## License

Text contributions are released under [CC BY 4.0](LICENSE). Pictures are not. The author keeps all rights, and the credit on the toolchanger page is the condition of use.
