---
{"dg-publish":true,"permalink":"/track/summer-2024-calendar/","tags":["tracking"],"noteIcon":"","created":"2024-06-10T07:12:00","updated":"2024-05-27 7:03:03 am"}
---

<style scope=" ">.tasksCalendar span {
	display: contents;
}
.tasksCalendar .buttons {
	cursor: default;
	width: 100%;
	height: 30px;
	display: flex;
	flex-wrap: nowrap;
	flex-direction: row;
	margin-bottom: 4px;
}
.tasksCalendar[view='list'] button.listView,
.tasksCalendar[view='week'] button.weekView,
.tasksCalendar[view='month'] button.monthView,
.tasksCalendar.filter button.filter {
	background: var(--background-modifier-active-hover);
}
body:not(.is-mobile) .tasksCalendar button.listView:hover,
body:not(.is-mobile) .tasksCalendar button.weekView:hover,
body:not(.is-mobile) .tasksCalendar button.monthView:hover,
body:not(.is-mobile) .tasksCalendar button.previous:hover,
body:not(.is-mobile) .tasksCalendar button.next:hover,
body:not(.is-mobile) .tasksCalendar button.current:hover,
body:not(.is-mobile) .tasksCalendar button.filter:hover,
body:not(.is-mobile) .tasksCalendar button.statistic:hover {
	background: var(--background-modifier-hover);
}
.tasksCalendar[view='list'] button.listView svg,
.tasksCalendar[view='month'] button.monthView svg,
.tasksCalendar[view='week'] button.weekView svg,
.tasksCalendar.filter button.filter svg {
	stroke: var(--icon-color-active) !important;
}
.tasksCalendar button {
	background-color: transparent;
	display: inline-flex;
	align-items: center;
	justify-content: center;
	cursor: pointer;
	border-radius: 5px;
	color: var(--icon-color);
	height: 30px;
	box-shadow: none;
	border: 1px solid var(--nav-item-background-active);
	font-weight: normal;
	font-size: 14px;
	background: var(--background-secondary);
	padding: 4px 6px;
	outline: none;
	user-select: none;
	white-space: nowrap;
	flex: 0;
}
.tasksCalendar button:nth-child(2),
.tasksCalendar button:nth-child(3),
.tasksCalendar button:nth-child(6) {
	border-top-right-radius: 0;
	border-bottom-right-radius: 0;
	border-right: 0.5px solid var(--nav-item-background-active);
	margin-right: 0;
}
.tasksCalendar button:nth-child(3),
.tasksCalendar button:nth-child(4),
.tasksCalendar button:nth-child(7) {
	border-top-left-radius: 0;
	border-bottom-left-radius: 0;
	border-left: 0.5px solid var(--nav-item-background-active);
	margin-left: 0;
}
.tasksCalendar .current {
	margin: 0 4px;
	display: inline;
	overflow: hidden;
	text-overflow: ellipsis;
	white-space: nowrap;
	flex: 1;
}
.tasksCalendar .current span:first-child {
	font-weight: bold;
	color: var(--icon-color);
}
.tasksCalendar .current span:last-child {
	font-weight: normal;
	color: var(--icon-color-active);
}
.tasksCalendar button:nth-child(1) {
	margin-right: 4px;
}
.tasksCalendar button:nth-child(8) {
	margin-left: 4px;
}
.tasksCalendar svg {
	height: var(--icon-size);
	width: var(--icon-size);
	stroke-width: var(--icon-stroke);
}
.tasksCalendar .statisticPopup,
.tasksCalendar .weekViewContext {
	display: none;
	border-radius: 5px;
	font-size: 10px;
	border: 1px solid var(--nav-item-background-active);
	position: absolute;
	height: auto;
	width: 150px;
	width: auto;
	background: var(--icon-color);
	margin: 0 !important;
	list-style: none;
	padding: 2px !important;
	z-index: 99;
	box-shadow: 0px 0px 10px 0px var(--nav-item-background-active);
	background: var(--background-secondary);
}
.tasksCalendar .statisticPopup {
	right: 0;
}
.tasksCalendar .weekViewContext {
	left: 65px;
}
.tasksCalendar .statisticPopup:before,
.tasksCalendar .weekViewContext:before {
	content: "";
	width: 0px;
	height: 0px;
	-webkit-transform:rotate(360deg);
	border-style: solid;
	border-width: 0 10px 10px 10px;
	border-color: transparent transparent var(--background-secondary) transparent;
	position: absolute;
}
.tasksCalendar .statisticPopup:before {
	top: -10px;
	right: 5px;
}
.tasksCalendar .weekViewContext:before {
	top: -10px;
	left: 5px;
}
.tasksCalendar .statisticPopup.active,
.tasksCalendar .weekViewContext.active {
	display: block;
}
.tasksCalendar .statisticPopup li,
.tasksCalendar .weekViewContext li {
	display: flex;
	flex-direction: row;
	flex-wrap: nowrap;
	align-items: center;
	height: auto;
	font-size: 14px;
	list-style: none;
	color: var(--text-normal);
	padding: 5px 10px;
	border-radius: 5px;
	cursor: pointer;
}
.tasksCalendar .statisticPopup li.active,
.tasksCalendar .weekViewContext li.active {
	background: var(--background-modifier-active-hover);
	color: var(--icon-color-active) !important;
}
body:not(.is-mobile) .tasksCalendar .statisticPopup li:not(.active):hover,
body:not(.is-mobile) .tasksCalendar .weekViewContext li:not(.active):hover {
	background: var(--background-modifier-hover);
}
.tasksCalendar .statisticPopup li.break,
.tasksCalendar .weekViewContext li.break {
	height: 1px !important;
	background: var(--nav-item-background-active);
	margin: 2px 5px !important;
	border-radius: 0 !important;
	padding: 0 !important;
}
.tasksCalendar .statisticPopup > div,
.tasksCalendar .weekViewContext > div {
	height: 13px;
	margin: auto 0;
}
.tasksCalendar button.statistic {
	position: relative;
}
.tasksCalendar button.statistic svg {
	stroke: var(--icon-color);
}
.tasksCalendar button.statistic[data-percentage="100"]:after {
	display: none !important;
}
.tasksCalendar button.statistic:after {
	content: attr(data-remaining);
	position: absolute;
	height: 14px;
	width: 14px;
	top: -8px;
	right: -8px;
	border-radius: 50%;
	text-align: center;
	line-height: 14px;
	font-size: 9px;
	font-weight: bold;
	border: 1px solid var(--nav-item-background-active);
	overflow: hidden;
	color: var(--icon-color);
	background: var(--background-secondary);
}
.tasksCalendar .weekViewContext .liIcon {
	display: grid !important;
	height: 18px;
	width: 18px;
	margin-right: 5px;
	padding: 2px;
}
.tasksCalendar .weekViewContext .liIcon .box {
	background: var(--icon-color);
	z-index: 1;
	display: grid;
	overflow: hidden;
	margin: 0.5px;
	border-radius: 1px;
}
.tasksCalendar .weekViewContext li.active .liIcon .box {
	background: var(--icon-color-active) !important;
}
.tasksCalendar .grid {
	overflow: hidden;
	cursor: default;
	width: 100%;
	height: 75vH;
}
.tasksCalendar .list {
	overflow-x: hidden;
	overflow-y: auto;
	cursor: default;
	width: 100%;
	height: 75vH;
}
.tasksCalendar .cell {
	z-index: 1;
	display: grid;
	grid-template-rows: auto 1fr;
	grid-template-columns: 1fr;
	overflow: hidden;
	margin: 1px 0;
}
.tasksCalendar .cellContent {
	overflow-x: hidden;
	overflow-y: auto;
	align-content: start;
	padding: 1px 0;
}
.tasksCalendar .cellContent::-webkit-scrollbar {
	display: none;
}
.tasksCalendar .cellName {
	display: block;
	font-weight: normal;
	padding: 0 2px;
	color: var(--text-normal);
	flex-shrink: 0;
	flex-grow: 0;
	white-space: nowrap;
	text-overflow: ellipsis;
	overflow: hidden;
	text-align: left;
	margin: 0;
	font-size: 14px;
	opacity: 0.8;
}
body:not(.is-mobile) .tasksCalendar .cellName:hover {
	opacity: 1;
}
.tasksCalendar .task {
	overflow: hidden;
	padding: 1px;
	background: var(--task-background);
	border-radius: 3px;
	overflow: hidden;
	margin: 1px 1px 2px 1px;
	font-size: 14px;
	opacity: 0.8;
	display: block;
}
body.theme-dark .tasksCalendar .task { color: var(--light-task-text-color); }
body.theme-light .tasksCalendar .task { color: var(--dark-task-text-color); }
body.theme-dark .tasksCalendar .task .note { color: var(--light-task-text-color); }
body.theme-light .tasksCalendar .task .note { color: var(--dark-task-text-color); }
body:not(.is-mobile) .tasksCalendar .task:hover {
	opacity: 1;
}
.tasksCalendar .task.hide {
	opacity: 0.2;
}
.tasksCalendar .task .inner {
	overflow: hidden;
	text-overflow: ellipsis;
	display: -webkit-box;
	-webkit-line-clamp: 1;
	-webkit-box-orient: vertical;
	text-decoration: none;
	word-break: break-all !important;
	-webkit-hyphens: none !important;
	line-height: 1.3;
	text-decoration: none !important;
	border-radius: 3px;
	overflow: hidden;
}
.tasksCalendar a {
	text-decoration: none !important;
}
.tasksCalendar .task .note {
	display: block;
	width: 100%;
	font-size: 9px;
	background: var(--task-background);
	padding: 1px;
	text-overflow: ellipsis;
	overflow: hidden;
	white-space: nowrap;
}
.tasksCalendar .task .icon {
	display: inline;
	width: 18px;
	height: 18px;
	text-align: center;
	margin-right: 3px;
}
.tasksCalendar .task .description {
	display: inline;
	padding: 1px;
}
.tasksCalendar .task .description:before {
	display: inline;
	content: attr(data-relative);
	margin-right: 3px;
	border-radius: 3px;
	margin-right: 3px;
	padding: 0 3px;
	font-size: 9px;
	vertical-align: middle;
}
.tasksCalendar .task.overdue .description:before {
	color: white;
	background: #ff443a;
}
.tasksCalendar .task:not(.overdue) .description:before {
	display: none;
	background: black;
	color: white;
}
.tasksCalendar .task.dailyNote .description:before,
.tasksCalendar .task.done .description:before,
.tasksCalendar .task.cancelled .description:before {
	display: none !important;
}
.tasksCalendar .task.cancelled .note,
.tasksCalendar .task.done .note {
	background: var(--nav-item-background-active) !important;
	color: var(--text-faint) !important;
}
.tasksCalendar .task.cancelled .description,
.tasksCalendar .task.done .description {
	text-decoration: line-through !important;
	color: var(--text-faint) !important;
}
.tasksCalendar .task.cancelled,
.tasksCalendar .task.done {
	background: none !important;
}
.tasksCalendar .task.overdue .inner {
	background: repeating-linear-gradient(45deg, var(--task-background), var(--task-background) 5px, transparent 5px, transparent 10px) !important;
}


/* Today & Weekends */
.tasksCalendar .cell.today .cellName {
	font-weight: bold;
	color: var(--text-normal);
	opacity: 1;
}
.tasksCalendar .cell[data-weekday="0"].today .cellName {
	font-weight: bold;
	color: var(--icon-color-active);
	opacity: 1;
}
.tasksCalendar[view='month'] .cell.today {
	background: var(--background-modifier-active-hover) !important;
	border: 1px solid hsla(var(--interactive-accent-hsl), 0.25) !important;
	border-radius: 5px;
}
.tasksCalendar[view='week'] .cell.today {
	background: var(--background-modifier-active-hover) !important;
	border: 1px solid hsla(var(--interactive-accent-hsl), 0.25) !important;
}
.tasksCalendar .cell[data-weekday="0"] .cellName,
.tasksCalendar .gridHead[data-weekday="0"] {
	color: var(--icon-color-active);
}


/* Month View */
.tasksCalendar[view='month'] .grid {
	display: grid;
	gap: 4px;
	grid-template-rows: 20px 1fr !important;
	grid-template-columns: 1fr !important;
}
.tasksCalendar[view='month'] .gridHeads {
	display: grid;
	grid-template-columns: 20px 1fr 1fr 1fr 1fr 1fr 1fr 1fr !important;
	width: 100%;
	height: 20px;
	border: 1px solid var(--nav-item-background-active);
	border-radius: 5px;
}
.tasksCalendar[view='month'] .gridHead {
	display: inline;
	box-sizing: border-box;
	overflow: hidden;
	text-align: center;
	font-weight: bold;
	text-overflow: ellipsis;
	white-space: nowrap;
	margin: 0;
	font-size: 14px;
	height: 20px;
	line-height: 20px;
	font-size: 10px;
}
.tasksCalendar[view='month'] .wrappers {
	display: grid;
	grid-template-rows: repeat(6, calc(100% / 6));
	grid-template-columns: 1fr !important;
	min-height: 0;
	height: calc(100% - 20px);
	gap: 4px 4px;
}
.tasksCalendar[view='month'] .wrappers,
.tasksCalendar[view='week'] .grid {
	position: relative;
}
.tasksCalendar[view='month'] .wrappers:before,
.tasksCalendar[view='week'] .grid:before,
.tasksCalendar[view='list'] .list:before {
	z-index: 0;
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
	font-size: 120px;
	font-weight: bold;
	color: var(--background-modifier-active-hover);
}
.tasksCalendar[view='month'] .wrappers:before,
.tasksCalendar[view='list'] .list:before {
	content: attr(data-month);
}
.tasksCalendar[view='week'] .grid:before {
	content: attr(data-week);
}
.tasksCalendar[view='month'] .wrapper {
	z-index: 1;
	display: grid;
	grid-template-rows: 1fr !important;
	grid-template-columns: 22px 1fr 1fr 1fr 1fr 1fr 1fr 1fr !important;
	width: 100%;
	height: 100%;
	border: 1px solid var(--nav-item-background-active);
	border-radius: 5px;
	overflow: hidden;
}
.tasksCalendar[view='month'] .wrapperButton {
	display: flex;
	writing-mode: vertical-lr;
	transform: rotate(180deg);
	background: none;
	text-align: center;
	align-items: center;
	justify-content: center;
	font-size: 10px;
	font-weight: normal;
	color: var(--text-normal);
	color: var(--icon-color-active);
	cursor: pointer;
	width: 100%;
	overflow: hidden;
	/* background: var(--background-primary); */
	background: var(--background-secondary);
}
.tasksCalendar[view='month'] .wrapperButton:hover {
	background: var(--background-modifier-hover);
}
.tasksCalendar[view='month'] .cell {
	margin: 0;
}
.tasksCalendar[view='month'] .prevMonth,
.tasksCalendar[view='month'] .nextMonth {
	background: var(--background-secondary);
}


/* Week view */
.tasksCalendar[view='week'] .grid {
	display: grid;
	gap: 2px 4px;
}
.tasksCalendar[view='week'] .cell {
	border: 1px solid var(--nav-item-background-active);
	border-radius: 5px;
	overflow: hidden;
}


/* List View */
.tasksCalendar[view='list'] .list {
	border: 1px solid var(--nav-item-background-active);
	border-radius: 5px;
}
.tasksCalendar[view='list'] .list .task,
.tasksCalendar[view='list'] .list .task.done,
.tasksCalendar[view='list'] .list .task .note,
.tasksCalendar[view='list'] .list .task.done .note{
	background: transparent !important;
}
.tasksCalendar[view='list'] .list .task .inner {
	display: flex !important;
	flex-direction: row;
	flex-wrap: nowrap;
	padding: 0 10px;
	white-space: nowrap;
}
.tasksCalendar[view='list'] .list .task .note {
	display: inline-block;
	width: 150px;
	flex-shrink: 0;
	flex-grow: 0;
}
.tasksCalendar[view='list'] .list .task .description {
	width: 100%;
	flex-shrink: 1;
	flex-grow: 1;
}
.tasksCalendar[view='list'] .list .task.done .note,
.tasksCalendar[view='list'] .list .task.done .description,
.tasksCalendar[view='list'] .list .task.cancelled .note,
.tasksCalendar[view='list'] .list .task.cancelled .description {
	color: var(--text-faint) !important;
}
.tasksCalendar[view='list'] .list .task .note,
.tasksCalendar[view='list'] .list .task .description {
	color: var(--task-color) !important;
	line-clamp: 0 !important;
	white-space: nowrap !important;
	text-overflow: ellipsis;
	overflow: hidden;
	font-size: 14px;
}
.tasksCalendar summary::marker,
.tasksCalendar summary::-webkit-details-marker {
	display: none !important;
	content: "" !important;
}
.tasksCalendar[view='list'] details.today {
	background: var(--background-modifier-active-hover);
	border: 1px solid hsla(var(--interactive-accent-hsl), 0.25);
}
.tasksCalendar[view='list'] details.today summary {
	font-weight: bold;
	background: none;
}
.tasksCalendar[view='list'] details.today .content {
	margin: 3px;
}
.tasksCalendar[view='list'] details {
	display: block;
	margin: 5px;
	border-radius: 5px;
	overflow: hidden;
	/*background: var(--background-secondary);*/
	border: 1px solid var(--nav-item-background-active);
}
.tasksCalendar[view='list'] summary {
	background: var(--background-secondary);
	padding: 0 10px;
	border-radius: 5px;
}
.tasksCalendar[view='list'] summary span.weekNr {
	font-size: 11px;
	color: var(--text-faint);
}


/* Style classes */
.tasksCalendar[view='week'].style1 .grid, .iconStyle1 { grid-template-columns: repeat(4, 1fr); grid-template-rows: repeat(6, 1fr); }
.tasksCalendar[view='week'].style1 .grid .cell:nth-child(1), .iconStyle1 .box:nth-child(1) { grid-area: 1 / 1 / 3 / 3; }
.tasksCalendar[view='week'].style1 .grid .cell:nth-child(2), .iconStyle1 .box:nth-child(2) { grid-area: 3 / 1 / 5 / 3; }
.tasksCalendar[view='week'].style1 .grid .cell:nth-child(3), .iconStyle1 .box:nth-child(3) { grid-area: 5 / 1 / 7 / 3; }
.tasksCalendar[view='week'].style1 .grid .cell:nth-child(4), .iconStyle1 .box:nth-child(4) { grid-area: 1 / 3 / 3 / 5; }
.tasksCalendar[view='week'].style1 .grid .cell:nth-child(5), .iconStyle1 .box:nth-child(5) { grid-area: 3 / 3 / 5 / 5; }
.tasksCalendar[view='week'].style1 .grid .cell:nth-child(6), .iconStyle1 .box:nth-child(6) { grid-area: 5 / 3 / 6 / 5; }
.tasksCalendar[view='week'].style1 .grid .cell:nth-child(7), .iconStyle1 .box:nth-child(7) { grid-area: 6 / 3 / 7 / 5; }
.tasksCalendar[view='week'].style2 .grid, .iconStyle2 { grid-template-columns: repeat(4, 1fr); grid-template-rows: repeat(6, 1fr); }
.tasksCalendar[view='week'].style2 .grid .cell:nth-child(1), .iconStyle2 .box:nth-child(1)  { grid-area: 1 / 1 / 3 / 3; }
.tasksCalendar[view='week'].style2 .grid .cell:nth-child(3), .iconStyle2 .box:nth-child(3)  { grid-area: 3 / 1 / 5 / 3; }
.tasksCalendar[view='week'].style2 .grid .cell:nth-child(5), .iconStyle2 .box:nth-child(5)  { grid-area: 5 / 1 / 7 / 3; }
.tasksCalendar[view='week'].style2 .grid .cell:nth-child(2), .iconStyle2 .box:nth-child(2)  { grid-area: 1 / 3 / 3 / 5; }
.tasksCalendar[view='week'].style2 .grid .cell:nth-child(4), .iconStyle2 .box:nth-child(4)  { grid-area: 3 / 3 / 5 / 5; }
.tasksCalendar[view='week'].style2 .grid .cell:nth-child(6), .iconStyle2 .box:nth-child(6)  { grid-area: 5 / 3 / 6 / 5; }
.tasksCalendar[view='week'].style2 .grid .cell:nth-child(7), .iconStyle2 .box:nth-child(7)  { grid-area: 6 / 3 / 7 / 5; }
.tasksCalendar[view='week'].style3 .grid, .iconStyle3 { grid-template-rows: 1fr 1fr 1fr 1fr 1fr 1fr 1fr; grid-template-columns: 1fr; }
.tasksCalendar[view='week'].style4 .grid, .iconStyle4 { grid-template-rows: 1fr; grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr; }
.tasksCalendar[view='week'].style5 .grid, .iconStyle5 { grid-template-columns: repeat(2, 1fr); grid-template-rows: repeat(10, 1fr); }
.tasksCalendar[view='week'].style5 .grid .cell:nth-child(1), .iconStyle5 .box:nth-child(1) { grid-area: 1 / 1 / 3 / 2; }
.tasksCalendar[view='week'].style5 .grid .cell:nth-child(2), .iconStyle5 .box:nth-child(2) { grid-area: 3 / 1 / 5 / 2; }
.tasksCalendar[view='week'].style5 .grid .cell:nth-child(3), .iconStyle5 .box:nth-child(3) { grid-area: 5 / 1 / 7 / 2; }
.tasksCalendar[view='week'].style5 .grid .cell:nth-child(4), .iconStyle5 .box:nth-child(4) { grid-area: 7 / 1 / 9 / 2; }
.tasksCalendar[view='week'].style5 .grid .cell:nth-child(5), .iconStyle5 .box:nth-child(5) { grid-area: 9 / 1 / 11 / 2; }
.tasksCalendar[view='week'].style5 .grid .cell:nth-child(6), .iconStyle5 .box:nth-child(6) { grid-area: 1 / 2 / 6 / 3; }
.tasksCalendar[view='week'].style5 .grid .cell:nth-child(7), .iconStyle5 .box:nth-child(7) { grid-area: 6 / 2 / 11 / 3; }
.tasksCalendar[view='week'].style6 .grid, .iconStyle6 { grid-template-columns: repeat(3, 1fr); grid-template-rows: repeat(10, 1fr); }
.tasksCalendar[view='week'].style6 .grid .cell:nth-child(1), .iconStyle6 .box:nth-child(1) { grid-area: 1 / 1 / 3 / 3; }
.tasksCalendar[view='week'].style6 .grid .cell:nth-child(2), .iconStyle6 .box:nth-child(2) { grid-area: 3 / 1 / 5 / 3; }
.tasksCalendar[view='week'].style6 .grid .cell:nth-child(3), .iconStyle6 .box:nth-child(3) { grid-area: 5 / 1 / 7 / 3; }
.tasksCalendar[view='week'].style6 .grid .cell:nth-child(4), .iconStyle6 .box:nth-child(4) { grid-area: 7 / 1 / 9 / 3; }
.tasksCalendar[view='week'].style6 .grid .cell:nth-child(5), .iconStyle6 .box:nth-child(5) { grid-area: 9 / 1 / 11 / 3; }
.tasksCalendar[view='week'].style6 .grid .cell:nth-child(6), .iconStyle6 .box:nth-child(6) { grid-area: 1 / 3 / 6 / 4; }
.tasksCalendar[view='week'].style6 .grid .cell:nth-child(7), .iconStyle6 .box:nth-child(7) { grid-area: 6 / 3 / 11 / 4; }
.tasksCalendar[view='week'].style7 .grid, .iconStyle7 { grid-template-columns: repeat(2, 1fr); grid-template-rows: repeat(8, 1fr); }
.tasksCalendar[view='week'].style7 .grid .cell:nth-child(1), .iconStyle7 .box:nth-child(1) { grid-area: 1 / 1 / 3 / 2; }
.tasksCalendar[view='week'].style7 .grid .cell:nth-child(2), .iconStyle7 .box:nth-child(2) { grid-area: 3 / 1 / 5 / 2; }
.tasksCalendar[view='week'].style7 .grid .cell:nth-child(3), .iconStyle7 .box:nth-child(3) { grid-area: 5 / 1 / 7 / 2; }
.tasksCalendar[view='week'].style7 .grid .cell:nth-child(4), .iconStyle7 .box:nth-child(4) { grid-area: 7 / 1 / 9 / 2; }
.tasksCalendar[view='week'].style7 .grid .cell:nth-child(5), .iconStyle7 .box:nth-child(5) { grid-area: 1 / 2 / 3 / 3; } 
.tasksCalendar[view='week'].style7 .grid .cell:nth-child(6), .iconStyle7 .box:nth-child(6) { grid-area: 3 / 2 / 6 / 3; } 
.tasksCalendar[view='week'].style7 .grid .cell:nth-child(7), .iconStyle7 .box:nth-child(7) { grid-area: 6 / 2 / 9 / 3; } 
.tasksCalendar[view='week'].style8 .grid, .iconStyle8 { grid-template-columns: repeat(3, 1fr); grid-template-rows: repeat(5, 1fr); }
.tasksCalendar[view='week'].style8 .grid .cell:nth-child(1), .iconStyle8 .box:nth-child(1) { grid-area: 1 / 1 / 3 / 2; }
.tasksCalendar[view='week'].style8 .grid .cell:nth-child(2), .iconStyle8 .box:nth-child(2) { grid-area: 1 / 2 / 3 / 3; }
.tasksCalendar[view='week'].style8 .grid .cell:nth-child(3), .iconStyle8 .box:nth-child(3) { grid-area: 1 / 3 / 3 / 4; }
.tasksCalendar[view='week'].style8 .grid .cell:nth-child(4), .iconStyle8 .box:nth-child(4) { grid-area: 3 / 1 / 5 / 2; }
.tasksCalendar[view='week'].style8 .grid .cell:nth-child(5), .iconStyle8 .box:nth-child(5) { grid-area: 3 / 2 / 5 / 3; }
.tasksCalendar[view='week'].style8 .grid .cell:nth-child(6), .iconStyle8 .box:nth-child(6) { grid-area: 3 / 3 / 5 / 4; }
.tasksCalendar[view='week'].style8 .grid .cell:nth-child(7), .iconStyle8 .box:nth-child(7) { grid-area: 5 / 1 / 6 / 4; }
.tasksCalendar[view='week'].style9 .grid, .iconStyle9 { grid-template-columns: repeat(10, 1fr); grid-template-rows: repeat(3, 1fr); }
.tasksCalendar[view='week'].style9 .grid .cell:nth-child(1), .iconStyle9 .box:nth-child(1) { grid-area: 1 / 1 / 3 / 3; } 
.tasksCalendar[view='week'].style9 .grid .cell:nth-child(2), .iconStyle9 .box:nth-child(2) { grid-area: 1 / 3 / 3 / 5; } 
.tasksCalendar[view='week'].style9 .grid .cell:nth-child(3), .iconStyle9 .box:nth-child(3) { grid-area: 1 / 5 / 3 / 7; } 
.tasksCalendar[view='week'].style9 .grid .cell:nth-child(4), .iconStyle9 .box:nth-child(4) { grid-area: 1 / 7 / 3 / 9; } 
.tasksCalendar[view='week'].style9 .grid .cell:nth-child(5), .iconStyle9 .box:nth-child(5) { grid-area: 1 / 9 / 3 / 11; } 
.tasksCalendar[view='week'].style9 .grid .cell:nth-child(6), .iconStyle9 .box:nth-child(6) { grid-area: 3 / 1 / 4 / 6; } 
.tasksCalendar[view='week'].style9 .grid .cell:nth-child(7), .iconStyle9 .box:nth-child(7) { grid-area: 3 / 6 / 4 / 11; } 
.tasksCalendar[view='week'].style10 .grid, .iconStyle10 { grid-template-columns: repeat(10, 1fr); grid-template-rows: repeat(3, 1fr); }
.tasksCalendar[view='week'].style10 .grid .cell:nth-child(1), .iconStyle10 .box:nth-child(1) { grid-area: 1 / 1 / 4 / 3; } 
.tasksCalendar[view='week'].style10 .grid .cell:nth-child(2), .iconStyle10 .box:nth-child(2) { grid-area: 1 / 3 / 4 / 5; } 
.tasksCalendar[view='week'].style10 .grid .cell:nth-child(3), .iconStyle10 .box:nth-child(3) { grid-area: 1 / 5 / 4 / 7; } 
.tasksCalendar[view='week'].style10 .grid .cell:nth-child(4), .iconStyle10 .box:nth-child(4) { grid-area: 1 / 7 / 3 / 9; } 
.tasksCalendar[view='week'].style10 .grid .cell:nth-child(5), .iconStyle10 .box:nth-child(5) { grid-area: 1 / 9 / 3 / 11; } 
.tasksCalendar[view='week'].style10 .grid .cell:nth-child(6), .iconStyle10 .box:nth-child(6) { grid-area: 3 / 7 / 4 / 9; } 
.tasksCalendar[view='week'].style10 .grid .cell:nth-child(7), .iconStyle10 .box:nth-child(7) { grid-area: 3 / 9 / 4 / 11; } 
.tasksCalendar[view='week'].style11 .grid, .iconStyle11 { grid-template-rows: 1fr; grid-template-columns: 1fr 1fr 1fr 1fr 1fr; }
.tasksCalendar[view='week'].style11 .grid { height: 300px }
.tasksCalendar[view='week'].style11 .cell[data-weekday="0"], .iconStyle11 { display: none !important }
.tasksCalendar[view='week'].style11 .cell[data-weekday="6"], .iconStyle11 { display: none !important }

/* Options classes */
.tasksCalendar.noIcons .task .icon { display: none !important; }
.tasksCalendar:not(.noFilename) .task.noNoteIcon .icon { display: none !important; }
.tasksCalendar.noFilename .task .note { display: none !important; }
.tasksCalendar.filter .task.done, .tasksCalendar.filter .task.cancelled { display: none !important; }
.tasksCalendar.filter #statisticDone { pointer-events: none !important; color: var(--text-faint) !important; }
.tasksCalendar.noScheduled .task.scheduled { display: none !important; }
.tasksCalendar.noStart .task.start { display: none !important; }
.tasksCalendar.noDue .task.due { display: none !important; }
.tasksCalendar.noDone .task.done { display: none !important; }
.tasksCalendar.noProcess .task.process { display: none !important; }
.tasksCalendar.noRecurrence .task.recurrence { display: none !important; }
.tasksCalendar.noOverdue .task.overdue { display: none !important; }
.tasksCalendar.noDailyNote .task.dailyNote { display: none !important; }
.tasksCalendar.noCellNameEvent .cellName { pointer-events: none !important; }
.tasksCalendar.noLayer .grid .wrappers:before,
.tasksCalendar.noLayer .grid:before,
.tasksCalendar.noLayer .list:before { display: none !important;}
.tasksCalendar.focusDone .task { opacity: 0.25 !important; }
.tasksCalendar.focusDone .task.done { opacity: 1 !important; }
.tasksCalendar.focusDue .task { opacity: 0.25 !important; }
.tasksCalendar.focusDue .task.due { opacity: 1 !important; }
.tasksCalendar.focusOverdue .task { opacity: 0.25 !important; }
.tasksCalendar.focusOverdue .task.overdue { opacity: 1 !important; }
.tasksCalendar.focusStart .task { opacity: 0.25 !important; }
.tasksCalendar.focusStart .task.start { opacity: 1 !important; }
.tasksCalendar.focusScheduled .task { opacity: 0.25 !important; }
.tasksCalendar.focusScheduled .task.scheduled { opacity: 1 !important; }
.tasksCalendar.focusRecurrence .task { opacity: 0.25 !important; }
.tasksCalendar.focusRecurrence .task.recurrence { opacity: 1 !important; }
.tasksCalendar.focusDailyNote .task { opacity: 0.25 !important; }
.tasksCalendar.focusDailyNote .task.dailyNote { opacity: 1 !important; }
.tasksCalendar.mini { max-width: 500px !important; margin: 0 auto; }
.tasksCalendar.mini .grid { height: 400px !important; }
.tasksCalendar.mini .gridHead,
.tasksCalendar.mini .cellName,
.tasksCalendar.mini .task,
.tasksCalendar.mini .wrapperButton { font-size: 9px !important; }
.tasksCalendar.mini .wrappers:before,
.tasksCalendar.mini .grid:before { font-size: 70px !important; }
.tasksCalendar.mini .statisticPopup li,
.tasksCalendar.mini .weekViewContext li { font-size: 9px !important; }
.tasksCalendar.noWeekNr .wrapperButton { visibility: hidden !important; width: 0 !important; }
.tasksCalendar.noWeekNr .gridHead:first-child { visibility: hidden !important; width: 0 !important; }
.tasksCalendar.noWeekNr .wrapper { grid-template-columns: 0px 1fr 1fr 1fr 1fr 1fr 1fr 1fr !important; }
.tasksCalendar.noWeekNr .gridHeads { grid-template-columns: 0px 1fr 1fr 1fr 1fr 1fr 1fr 1fr !important; }
.tasksCalendar.noWeekNr .list .weekNr { display: none !important; }
.tasksCalendar.lineClamp1 .task .inner { -webkit-line-clamp: 1 !important; white-space: nowrap !important; }
.tasksCalendar.lineClamp2 .task .inner { -webkit-line-clamp: 2 !important; }
.tasksCalendar.lineClamp3 .task .inner { -webkit-line-clamp: 3 !important; }
.tasksCalendar.noLineClamp .task .inner { display: block !important; }
.tasksCalendar.noOverdueFlag .task .description:before { display: none !important; }

/* Mobile View */
body.is-mobile .tasksCalendar .gridHead, body.is-mobile .tasksCalendar .cellName, body.is-mobile .tasksCalendar .task { font-size: 9px; }
body.is-mobile .tasksCalendar[view='week']:not(.style4) .cellName,
body.is-mobile .tasksCalendar[view='week']:not(.style4) .task { font-size: 13px !important; }
body.is-mobile .tasksCalendar .statisticPopup li { font-size: 13px !important; }

/*# sourceURL=app://obsidian.md/PERSONAL/tasksCalendar/view.css */</style><div class="tasksCalendar style1 noWeekNr noIcons noFilename" id="tasksCalendar1716831558926" view="month" style="position:relative;-webkit-user-select:none!important"><span><div class="buttons"><span><button class="filter"><svg stroke-linejoin="round" stroke-linecap="round" stroke-width="2" stroke="currentColor" fill="none" viewBox="0 0 24 24" height="24" width="24" xmlns="http://www.w3.org/2000/svg"><polygon points="22 3 2 3 10 12.46 10 19 14 21 14 12.46 22 3"></polygon></svg></button><button title="List" class="listView"><svg stroke-linejoin="round" stroke-linecap="round" stroke-width="2" stroke="currentColor" fill="none" viewBox="0 0 24 24" height="24" width="24" xmlns="http://www.w3.org/2000/svg"><line y2="6" x2="21" y1="6" x1="8"></line><line y2="12" x2="21" y1="12" x1="8"></line><line y2="18" x2="21" y1="18" x1="8"></line><line y2="6" x2="3.01" y1="6" x1="3"></line><line y2="12" x2="3.01" y1="12" x1="3"></line><line y2="18" x2="3.01" y1="18" x1="3"></line></svg></button><button title="Month" class="monthView"><svg stroke-linejoin="round" stroke-linecap="round" stroke-width="2" stroke="currentColor" fill="none" viewBox="0 0 24 24" height="24" width="24" xmlns="http://www.w3.org/2000/svg"><rect ry="2" rx="2" height="18" width="18" y="4" x="3"></rect><line y2="6" x2="16" y1="2" x1="16"></line><line y2="6" x2="8" y1="2" x1="8"></line><line y2="10" x2="21" y1="10" x1="3"></line><path d="M8 14h.01"></path><path d="M12 14h.01"></path><path d="M16 14h.01"></path><path d="M8 18h.01"></path><path d="M12 18h.01"></path><path d="M16 18h.01"></path></svg></button><button title="Week" class="weekView"><svg stroke-linejoin="round" stroke-linecap="round" stroke-width="2" stroke="currentColor" fill="none" viewBox="0 0 24 24" height="24" width="24" xmlns="http://www.w3.org/2000/svg"><rect ry="2" rx="2" height="18" width="18" y="4" x="3"></rect><line y2="6" x2="16" y1="2" x1="16"></line><line y2="6" x2="8" y1="2" x1="8"></line><line y2="10" x2="21" y1="10" x1="3"></line><path d="M17 14h-6"></path><path d="M13 18H7"></path><path d="M7 14h.01"></path><path d="M17 18h.01"></path></svg></button><button class="current"><span>June</span><span> 2024</span></button><button class="previous"><svg stroke-linejoin="round" stroke-linecap="round" stroke-width="2" stroke="currentColor" fill="none" viewBox="0 0 24 24" height="24" width="24" xmlns="http://www.w3.org/2000/svg"><line y2="12" x2="5" y1="12" x1="19"></line><polyline points="12 19 5 12 12 5"></polyline></svg></button><button class="next"><svg stroke-linejoin="round" stroke-linecap="round" stroke-width="2" stroke="currentColor" fill="none" viewBox="0 0 24 24" height="24" width="24" xmlns="http://www.w3.org/2000/svg"><line y2="12" x2="19" y1="12" x1="5"></line><polyline points="12 5 19 12 12 19"></polyline></svg></button><button class="statistic" data-percentage="100" data-remaining="0"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 10V6a2 2 0 0 0-2-2H5a2 2 0 0 0-2 2v14c0 1.1.9 2 2 2h7"></path><path d="M16 2v4"></path><path d="M8 2v4"></path><path d="M3 10h18"></path><path d="M21.29 14.7a2.43 2.43 0 0 0-2.65-.52c-.3.12-.57.3-.8.53l-.34.34-.35-.34a2.43 2.43 0 0 0-2.65-.53c-.3.12-.56.3-.79.53-.95.94-1 2.53.2 3.74L17.5 22l3.6-3.55c1.2-1.21 1.14-2.8.19-3.74Z"></path></svg></button></span></div><ul class="statisticPopup"><span><li data-group="done" id="statisticDone">✅ Done: 0/0</li><li data-group="due" id="statisticDue">📅 Due: 0</li><li data-group="overdue" id="statisticOverdue">⚠️ Overdue: 0</li><li class="break"></li><li data-group="start" id="statisticStart">🛫 Start: 47</li><li data-group="scheduled" id="statisticScheduled">⏳ Scheduled: 0</li><li data-group="recurrence" id="statisticRecurrence">🔁 Recurrence: 0</li><li class="break"></li><li data-group="dailyNote" id="statisticDailyNote">📄 Daily Notes: 0</li></span></ul><ul class="weekViewContext"><span><li data-style="style1" class="active"><div class="liIcon iconStyle1"><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div></div>Style 1</li><li data-style="style2"><div class="liIcon iconStyle2"><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div></div>Style 2</li><li data-style="style3"><div class="liIcon iconStyle3"><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div></div>Style 3</li><li data-style="style4"><div class="liIcon iconStyle4"><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div></div>Style 4</li><li data-style="style5"><div class="liIcon iconStyle5"><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div></div>Style 5</li><li data-style="style6"><div class="liIcon iconStyle6"><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div></div>Style 6</li><li data-style="style7"><div class="liIcon iconStyle7"><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div></div>Style 7</li><li data-style="style8"><div class="liIcon iconStyle8"><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div></div>Style 8</li><li data-style="style9"><div class="liIcon iconStyle9"><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div></div>Style 9</li><li data-style="style10"><div class="liIcon iconStyle10"><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div></div>Style 10</li><li data-style="style11"><div class="liIcon iconStyle11"><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div><div class="box"></div></div>Style 11</li></span></ul><div class="grid"><span><div class="gridHeads"><div class="gridHead"></div><div data-weekday="0" class="gridHead">Sun</div><div data-weekday="1" class="gridHead">Mon</div><div data-weekday="2" class="gridHead">Tue</div><div data-weekday="3" class="gridHead">Wed</div><div data-weekday="4" class="gridHead">Thu</div><div data-weekday="5" class="gridHead">Fri</div><div data-weekday="6" class="gridHead">Sat</div></div><div data-month="Jun" class="wrappers"><div class="wrapper"><div data-year="2024" data-week="22" class="wrapperButton">W22</div><div data-weekday="0" class="cell prevMonth"><a href="2024-05-26" class="internal-link cellName" target="_blank" rel="noopener">26</a><div class="cellContent"></div></div><div data-weekday="1" class="cell prevMonth"><a href="2024-05-27" class="internal-link cellName" target="_blank" rel="noopener">27</a><div class="cellContent"></div></div><div data-weekday="2" class="cell prevMonth"><a href="2024-05-28" class="internal-link cellName" target="_blank" rel="noopener">28</a><div class="cellContent"></div></div><div data-weekday="3" class="cell prevMonth"><a href="2024-05-29" class="internal-link cellName" target="_blank" rel="noopener">29</a><div class="cellContent"></div></div><div data-weekday="4" class="cell prevMonth"><a href="2024-05-30" class="internal-link cellName" target="_blank" rel="noopener">30</a><div class="cellContent"></div></div><div data-weekday="5" class="cell prevMonth"><a href="2024-05-31" class="internal-link cellName" target="_blank" rel="noopener">31</a><div class="cellContent"></div></div><div data-weekday="6" class="cell currentMonth newMonth"><a href="2024-06-01" class="internal-link cellName" target="_blank" rel="noopener">1. Jun</a><div class="cellContent"></div></div></div><div class="wrapper"><div data-year="2024" data-week="23" class="wrapperButton">W23</div><div data-weekday="0" class="cell currentMonth"><a href="2024-06-02" class="internal-link cellName" target="_blank" rel="noopener">2</a><div class="cellContent"></div></div><div data-weekday="1" class="cell currentMonth"><a href="2024-06-03" class="internal-link cellName" target="_blank" rel="noopener">3</a><div class="cellContent"></div></div><div data-weekday="2" class="cell currentMonth"><a href="2024-06-04" class="internal-link cellName" target="_blank" rel="noopener">4</a><div class="cellContent"></div></div><div data-weekday="3" class="cell currentMonth"><a href="2024-06-05" class="internal-link cellName" target="_blank" rel="noopener">5</a><div class="cellContent"></div></div><div data-weekday="4" class="cell currentMonth"><a href="2024-06-06" class="internal-link cellName" target="_blank" rel="noopener">6</a><div class="cellContent"></div></div><div data-weekday="5" class="cell currentMonth"><a href="2024-06-07" class="internal-link cellName" target="_blank" rel="noopener">7</a><div class="cellContent"></div></div><div data-weekday="6" class="cell currentMonth"><a href="2024-06-08" class="internal-link cellName" target="_blank" rel="noopener">8</a><div class="cellContent"></div></div></div><div class="wrapper"><div data-year="2024" data-week="24" class="wrapperButton">W24</div><div data-weekday="0" class="cell currentMonth"><a href="2024-06-09" class="internal-link cellName" target="_blank" rel="noopener">9</a><div class="cellContent"></div></div><div data-weekday="1" class="cell currentMonth"><a href="2024-06-10" class="internal-link cellName" target="_blank" rel="noopener">10</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - School Work" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - School Work </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - School Work" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - School Work </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - School Work" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - School Work </div></div></div></a></div></div><div data-weekday="2" class="cell currentMonth"><a href="2024-06-11" class="internal-link cellName" target="_blank" rel="noopener">11</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - School Work" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - School Work </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - School Work" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - School Work </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - School Work" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - School Work </div></div></div></a></div></div><div data-weekday="3" class="cell currentMonth"><a href="2024-06-12" class="internal-link cellName" target="_blank" rel="noopener">12</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - School Work" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - School Work </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - School Work" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - School Work </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - School Work" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - School Work </div></div></div></a></div></div><div data-weekday="4" class="cell currentMonth"><a href="2024-06-13" class="internal-link cellName" target="_blank" rel="noopener">13</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - School Work" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - School Work</div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - School Work" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - School Work </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - (https://projects.raspberrypi.org/en/collections/scratch)" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - (https://projects.raspberrypi.org/en/collections/scratch) </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - School Work" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - School Work </div></div></div></a></div></div><div data-weekday="5" class="cell currentMonth"><a href="2024-06-14" class="internal-link cellName" target="_blank" rel="noopener">14</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - (https://projects.raspberrypi.org/en/collections/html_and_css)" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - (https://projects.raspberrypi.org/en/collections/html_and_css) </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - (https://codeclubworld.org/launch/new)" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - (https://codeclubworld.org/launch/new) </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - (https://codeclubworld.org/launch/new)" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - (https://codeclubworld.org/launch/new) </div></div></div></a></div></div><div data-weekday="6" class="cell currentMonth"><a href="2024-06-15" class="internal-link cellName" target="_blank" rel="noopener">15</a><div class="cellContent"></div></div></div><div class="wrapper"><div data-year="2024" data-week="25" class="wrapperButton">W25</div><div data-weekday="0" class="cell currentMonth"><a href="2024-06-16" class="internal-link cellName" target="_blank" rel="noopener">16</a><div class="cellContent"></div></div><div data-weekday="1" class="cell currentMonth"><a href="2024-06-17" class="internal-link cellName" target="_blank" rel="noopener">17</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - Prep Golf Camp (1)" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - Prep Golf Camp (1) </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - STP Camp" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - STP Camp </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - STP Camp" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - STP Camp </div></div></div></a></div></div><div data-weekday="2" class="cell currentMonth"><a href="2024-06-18" class="internal-link cellName" target="_blank" rel="noopener">18</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - Prep Golf Camp (1)" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - Prep Golf Camp (1) </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - STP Camp" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - STP Camp </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - STP Camp" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - STP Camp </div></div></div></a></div></div><div data-weekday="3" class="cell currentMonth"><a href="2024-06-19" class="internal-link cellName" target="_blank" rel="noopener">19</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;📷&quot;&nbsp;Summer 2024: D - Yes Day with Mommy" style="--task-background:#fec60133;--task-color:#fec601;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"📷"&nbsp;Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - Yes Day with Mommy </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - STP Camp" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - STP Camp </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - STP Camp" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - STP Camp </div></div></div></a></div></div><div data-weekday="4" class="cell currentMonth"><a href="2024-06-20" class="internal-link cellName" target="_blank" rel="noopener">20</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - Prep Golf Camp (1)" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - Prep Golf Camp (1) </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - STP Camp" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - STP Camp </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - STP Camp" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - STP Camp </div></div></div></a></div></div><div data-weekday="5" class="cell currentMonth"><a href="2024-06-21" class="internal-link cellName" target="_blank" rel="noopener">21</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - Prep Golf Camp (1)" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - Prep Golf Camp (1) </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - STP Camp" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - STP Camp </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - STP Camp" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - STP Camp </div></div></div></a></div></div><div data-weekday="6" class="cell currentMonth"><a href="2024-06-22" class="internal-link cellName" target="_blank" rel="noopener">22</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;📷&quot;&nbsp;Summer 2024: Gianni 8th Grade Grad Party" style="--task-background:#fec60133;--task-color:#fec601;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"📷"&nbsp;Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">Gianni 8th Grade Grad Party </div></div></div></a></div></div></div><div class="wrapper"><div data-year="2024" data-week="26" class="wrapperButton">W26</div><div data-weekday="0" class="cell currentMonth"><a href="2024-06-23" class="internal-link cellName" target="_blank" rel="noopener">23</a><div class="cellContent"></div></div><div data-weekday="1" class="cell currentMonth"><a href="2024-06-24" class="internal-link cellName" target="_blank" rel="noopener">24</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - Prep Golf Camp (2)" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - Prep Golf Camp (2) </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - School Work" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - School Work </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;📷&quot;&nbsp;Summer 2024: G - Yes Day with Papa" style="--task-background:#fec60133;--task-color:#fec601;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"📷"&nbsp;Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - Yes Day with Papa </div></div></div></a></div></div><div data-weekday="2" class="cell currentMonth"><a href="2024-06-25" class="internal-link cellName" target="_blank" rel="noopener">25</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - Prep Golf Camp (2)" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - Prep Golf Camp (2) </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - School Work" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - School Work </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - School Work" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - School Work </div></div></div></a></div></div><div data-weekday="3" class="cell currentMonth"><a href="2024-06-26" class="internal-link cellName" target="_blank" rel="noopener">26</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - Prep Golf Camp (2)" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - Prep Golf Camp (2) </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - School Work" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - School Work </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - School Work" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - School Work </div></div></div></a></div></div><div data-weekday="4" class="cell currentMonth"><a href="2024-06-27" class="internal-link cellName" target="_blank" rel="noopener">27</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - Prep Golf Camp (2)" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - Prep Golf Camp (2) </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - (https://codeclubworld.org/launch/new)" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - (https://codeclubworld.org/launch/new) </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - (https://codeclubworld.org/launch/new)" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - (https://codeclubworld.org/launch/new) </div></div></div></a></div></div><div data-weekday="5" class="cell currentMonth"><a href="2024-06-28" class="internal-link cellName" target="_blank" rel="noopener">28</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - Prep Golf Camp (2)" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - Prep Golf Camp (2) </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - (https://projects.raspberrypi.org/en/collections/scratch)" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - (https://projects.raspberrypi.org/en/collections/scratch) </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - (https://projects.raspberrypi.org/en/collections/scratch)" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - (https://projects.raspberrypi.org/en/collections/scratch) </div></div></div></a></div></div><div data-weekday="6" class="cell currentMonth"><a href="2024-06-29" class="internal-link cellName" target="_blank" rel="noopener">29</a><div class="cellContent"></div></div></div><div class="wrapper"><div data-year="2024" data-week="27" class="wrapperButton">W27</div><div data-weekday="0" class="cell currentMonth"><a href="2024-06-30" class="internal-link cellName" target="_blank" rel="noopener">30</a><div class="cellContent"></div></div><div data-weekday="1" class="cell nextMonth newMonth"><a href="2024-07-01" class="internal-link cellName" target="_blank" rel="noopener">1. Jul</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;📷&quot;&nbsp;Summer 2024: D - Yes Day with Papa" style="--task-background:#fec60133;--task-color:#fec601;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"📷"&nbsp;Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - Yes Day with Papa </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - School Work" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - School Work </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - School Work" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - School Work </div></div></div></a></div></div><div data-weekday="2" class="cell nextMonth"><a href="2024-07-02" class="internal-link cellName" target="_blank" rel="noopener">2</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - School Work" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - School Work </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - School Work" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - School Work </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - School Work" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - School Work </div></div></div></a></div></div><div data-weekday="3" class="cell nextMonth"><a href="2024-07-03" class="internal-link cellName" target="_blank" rel="noopener">3</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - Dentist" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - Dentist </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Nico Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🤌🏻&quot;&nbsp;Nico Summer 2024: D - School Work" style="--task-background:#2364aa33;--task-color:#2364aa;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🤌🏻"&nbsp;Nico Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">D - School Work </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Ella - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🪁&quot;&nbsp;Ella - Summer 2024: E - School Work" style="--task-background:#d78a7633;--task-color:#d78a76;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🪁"&nbsp;Ella - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">E - School Work </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - Dentist" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - Dentist </div></div></div></a><a href="PERSONAL/tasksCalendar/Summer24/Gianluca - Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;🎯&quot;&nbsp;Gianluca - Summer 2024: G - School Work" style="--task-background:#37963433;--task-color:#379634;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"🎯"&nbsp;Gianluca - Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G - School Work </div></div></div></a></div></div><div data-weekday="4" class="cell nextMonth"><a href="2024-07-04" class="internal-link cellName" target="_blank" rel="noopener">4</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;📷&quot;&nbsp;Summer 2024: Holiday - 4th of July" style="--task-background:#fec60133;--task-color:#fec601;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"📷"&nbsp;Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">Holiday - 4th of July </div></div></div></a></div></div><div data-weekday="5" class="cell nextMonth"><a href="2024-07-05" class="internal-link cellName" target="_blank" rel="noopener">5</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;📷&quot;&nbsp;Summer 2024: Movies" style="--task-background:#fec60133;--task-color:#fec601;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"📷"&nbsp;Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">Movies </div></div></div></a></div></div><div data-weekday="6" class="cell nextMonth"><a href="2024-07-06" class="internal-link cellName" target="_blank" rel="noopener">6</a><div class="cellContent"><a href="PERSONAL/tasksCalendar/Summer24/Summer 2024.md" class="internal-link" target="_blank" rel="noopener"><div title="&quot;📷&quot;&nbsp;Summer 2024: G &amp; E Bday" style="--task-background:#fec60133;--task-color:#fec601;--dark-task-text-color:#ffffff;--light-task-text-color:#ffffff" class="task start"><div class="inner"><div class="note">"📷"&nbsp;Summer 2024</div><div class="icon">🛫</div><div data-relative="" class="description">G &amp; E Bday </div></div></div></a></div></div></div></div></span></div></span></div>

 



## Reference
- https://github.com/702573N/Obsidian-Tasks-Calendar
- [[PERSONAL/tasksCalendar/README\|README]]

Filter by tag
```
pages: "dv.pages().file.where(f=>f.tags.includes('#summer24') || f.tags.includes('#summer24')).where(f=>f.folder != 'Summer24').tasks"
```

Multiple Options
```
await dv.view("tasksCalendar", {pages: "", view: "month", firstDayOfWeek: "1", options: "noDailyNote noFilename style1"})
```

Options
```
options: "noCellNameEvent"
options: "lineClamp1"
options: "lineClamp2"
options: "lineClamp3"
options: "noLineClamp"
```